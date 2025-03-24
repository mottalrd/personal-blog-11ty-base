---
title: "Dockerized Rails Capybara tests on top of Selenium"
date: 2016-05-31
categories: 
  - "article"
tags: 
  - "capybara"
  - "docker"
  - "rails"
  - "ruby"
  - "selenium"
---

If you use Docker to deploy your Rails application you may want to use the same infrastructure to run your tests.

However the setup of your Selenium browser tests is far from obvious with Rails and Docker and may generate some confusion \[note\]StackOverflow: Dockerized selenium browser cannot access Capybara test url\[/note\] \[note\]StackOverflow: How to configure Capybara to run tests in a dockerized Selenium Grid?\[/note\] \[note\]A gist file with the same setup presented here\[/note\] \[note\]Another blog post on the same topic\[/note\] \[note\]Docker compose tutorial\[/note\].

The short answer is available in this repository on Github. For the long answer keep reading this blog post for a step by step tutorial!

# Dockerize Rails

Let's start by creating a Docker container to run your application. First we create a simple rails hello world app with the following commands:

```
# In your console
rails new test_app
```

```
# routes.rb
root 'hello_world#index'
```

```
# app/controller/hello_world_controller.rb
class HelloWorldController < ApplicationController
end

```

```
# app/views/hello_world/index.html.erb
Hello World
```

then we add the following to your Gemfile :

```
group :test do
  gem 'capybara'
  gem 'rspec-rails'
  gem 'selenium-webdriver'
end
```

Run bundle install  and bundle exec rails server  to make sure that our app is accessible at http://locahost:3000 . Also run rails generate rspec:install to initialize the spec directory.

We will now use the Gemfile  and the Gemfile.lock to set up of our Docker container. Let's create a Dockerfile in the root of the project with the following:

```
FROM ruby:latest
RUN apt-get update -qq && apt-get install -y build-essential nodejs

RUN mkdir /app
WORKDIR /app
COPY Gemfile Gemfile
COPY Gemfile.lock Gemfile.lock
RUN bundle install

CMD ["rails", "server", "-b", "0.0.0.0"]

```

The Dockerfile downloads the Ruby image called ruby:latest  and installs build-essential , nodejs and the gems specified in our Gemfile including Rails.

# Connect to a remote Selenium server

To run our tests we need a Selenium server running somewhere. By default the capybara  and selenium-webdriver gems spawn the selenium server automatically for us when we run our specs. But nothing stops us to select a different remote selenium server! Let's do that.

First go to http://www.seleniumhq.org/download/, download the latest tar and run the server with:

```
java -jar selenium-server-standalone-.jar
```

Now connect Capybara with the Selenium server we just started. Inside rails\_helper.rb add the following:

```
Capybara.javascript_driver = :selenium_remote_firefox
Capybara.register_driver "selenium_remote_firefox".to_sym do |app|
  Capybara::Selenium::Driver.new(app, browser: :remote, url: "http://localhost:4444/wd/hub", desired_capabilities: :firefox)
end

```

This will instruct Capybara to connect to the remote Selenium instance we are running. Finally add to the RSpec configuration the following lines:

```
RSpec.configure do |config|
  [...other conf...]

  config.before(:each) do
    Capybara.app_host = "http://localhost:#{Capybara.current_session.server.port}"
  end

  config.after(:each) do
    Capybara.reset_sessions!
    Capybara.use_default_driver
    Capybara.app_host = nil
  end
end

```

This will tell the Selenium server that the app it must visit is the one spawned by Capybara in our localhost. If you run bundle exec rspec  you should see the following in the Selenium server output:

```
19:02:02.207 INFO - Selenium Server is up and running
19:09:42.174 INFO - Executing: [new session: Capabilities [{rotatable=false, nativeEvents=false, browserName=firefox, takesScreenshot=true, javascriptEnabled=true, version=, platform=ANY, cssSelectorsEnabled=true}]])
19:09:42.198 INFO - Creating a new session for Capabilities [{rotatable=false, nativeEvents=false, browserName=firefox, takesScreenshot=true, javascriptEnabled=true, version=, platform=ANY, cssSelectorsEnabled=true}]
19:09:46.069 INFO - Done: [new session: Capabilities [{rotatable=false, nativeEvents=false, browserName=firefox, takesScreenshot=true, javascriptEnabled=true, version=, platform=ANY, cssSelectorsEnabled=true}]]
19:09:46.081 INFO - Executing: [get: http://localhost:57193/])
19:09:46.940 INFO - Done: [get: http://localhost:57193/]
19:09:46.953 INFO - Executing: [find elements: By.xpath: /html])
19:09:47.046 INFO - Done: [find elements: By.xpath: /html]
19:09:47.059 INFO - Executing: [is displayed: 0 [[FirefoxDriver: firefox on MAC (e536aaa9-930d-e544-849f-35739e1519c5)] -> xpath: /html]])
19:09:47.088 INFO - Done: [is displayed: 0 [[FirefoxDriver: firefox on MAC (e536aaa9-930d-e544-849f-35739e1519c5)] -> xpath: /html]]
19:09:47.094 INFO - Executing: [get text: 0 [[FirefoxDriver: firefox on MAC (e536aaa9-930d-e544-849f-35739e1519c5)] -> xpath: /html]])
19:09:47.108 INFO - Done: [get text: 0 [[FirefoxDriver: firefox on MAC (e536aaa9-930d-e544-849f-35739e1519c5)] -> xpath: /html]]
19:09:47.122 INFO - Executing: [delete all cookies])
19:09:47.136 INFO - Done: [delete all cookies]
19:09:47.142 INFO - Executing: [get: about:blank])
19:09:47.178 INFO - Done: [get: about:blank]
19:09:47.184 INFO - Executing: [find elements: By.xpath: /html/body/*])
19:09:47.194 INFO - Done: [find elements: By.xpath: /html/body/*]
19:09:47.201 INFO - Executing: [delete session: bde150ad-b376-45ea-b46b-5e6c82af97fa])
19:09:47.349 INFO - Done: [delete session: bde150ad-b376-45ea-b46b-5e6c82af97fa]
```

The server correctly received the calls from Capybara, visited the test app and completed the test successfully.

# Dockerize Selenium

The next step is to dockerize our Selenium server to run our browser tests inside a Docker container instead of our localhost . First, we need to create a docker-compose  file to run our application:

```
version: '2'
services:
  test:
    build: .
    command: bundle exec rspec
    container_name: test_app
    environment:
      - SELENIUM_REMOTE_HOST=selenium
    volumes:
      - .:/app
    depends_on:
      - selenium
  selenium:
    image: selenium/standalone-firefox
    container_name: selenium

```

The app has two services running inside the corresponding containers. The test service is running the rails container specified in our Dockerfile . The build entry specifies the location of the Dockerfile. The command entry specifies the command to execute when the service is invoked. In our case we want to run our tests. container\_name, environment and depends\_on  are self explicative. Finally the volumes instruction link our code into the container. Finally, the Selenium service is pretty easy to set up because there is a dockerized version of the server ready for us in selenium/standalone-firefox !

Let's now go back to our rails\_helper . We need the following to use the Selenium remote server:

```
if ENV['SELENIUM_REMOTE_HOST']
  Capybara.javascript_driver = :selenium_remote_firefox
  Capybara.register_driver "selenium_remote_firefox".to_sym do |app|
    Capybara::Selenium::Driver.new(
      app,
      browser: :remote,
      url: "http://#{ENV['SELENIUM_REMOTE_HOST']}:4444/wd/hub",
      desired_capabilities: :firefox)
  end
end
```

Notice that Docker by default makes the Selenium service available at the http://selenium host using the name specified in the docker-compose file. The port is the default one.

The RSpec configuration changes as follows:

```
RSpec.configure do |config|
  [...other config...]

  config.before(:each) do
    if /selenium_remote/.match Capybara.current_driver.to_s
      ip = `/sbin/ip route|awk '/scope/ { print $9 }'`
      ip = ip.gsub "\n", ""
      Capybara.server_port = "3000"
      Capybara.server_host = ip
      Capybara.app_host = "http://#{Capybara.current_session.server.host}:#{Capybara.current_session.server.port}"
    end
  end

  config.after(:each) do
    Capybara.reset_sessions!
    Capybara.use_default_driver
    Capybara.app_host = nil
  end
end

```

You may be surprised by these four magic lines:

```
ip = `/sbin/ip route|awk '/scope/ { print $9 }'`
ip = ip.gsub "\n", ""
Capybara.server_port = "3000"
Capybara.server_host = ip

```

these instructions retrieve the ip address of the container and pass it to Capybara and in turn to Selenium such that it will be able to retrieve the pages to test. In the basic Selenium remote example this configuration was not necessary because our test app was running on our localhost.

# Lunch the tests!

To run our tests at this point all we need is:

```
docker-compose up
```

and you should see something similar to the following:

```
:capybara-on-dockerized-selenium (master *+)$ docker-compose up
Creating network "capybaraondockerizedselenium_default" with the default driver
Creating selenium
Creating test_app
Attaching to selenium, test_app
selenium    | 11:33:18.295 INFO - Launching a standalone Selenium Server
selenium    | 11:33:18.413 INFO - Java: Oracle Corporation 25.03-b03
selenium    | 11:33:18.417 INFO - OS: Linux 4.4.8-boot2docker amd64
selenium    | 11:33:18.471 INFO - v2.53.0, with Core v2.53.0. Built from revision 35ae25b
selenium    | 11:33:18.825 INFO - Driver provider org.openqa.selenium.ie.InternetExplorerDriver registration is skipped:
selenium    | registration capabilities Capabilities [{ensureCleanSession=true, browserName=internet explorer, version=, platform=WINDOWS}] does not match the current platform LINUX
selenium    | 11:33:18.836 INFO - Driver provider org.openqa.selenium.edge.EdgeDriver registration is skipped:
selenium    | registration capabilities Capabilities [{browserName=MicrosoftEdge, version=, platform=WINDOWS}] does not match the current platform LINUX
selenium    | 11:33:18.837 INFO - Driver class not found: com.opera.core.systems.OperaDriver
selenium    | 11:33:18.840 INFO - Driver provider com.opera.core.systems.OperaDriver is not registered
selenium    | 11:33:18.850 INFO - Driver provider org.openqa.selenium.safari.SafariDriver registration is skipped:
selenium    | registration capabilities Capabilities [{browserName=safari, version=, platform=MAC}] does not match the current platform LINUX
selenium    | 11:33:18.860 INFO - Driver class not found: org.openqa.selenium.htmlunit.HtmlUnitDriver
selenium    | 11:33:18.861 INFO - Driver provider org.openqa.selenium.htmlunit.HtmlUnitDriver is not registered
selenium    | 11:33:19.151 INFO - RemoteWebDriver instances should connect to: http://127.0.0.1:4444/wd/hub
selenium    | 11:33:19.157 INFO - Selenium Server is up and running
test_app    | Running via Spring preloader in process 17
test_app    | /app/db/schema.rb doesn't exist yet. Run `rake db:migrate` to create it, then try again. If you do not intend to use a database, you should instead alter /app/config/application.rb to limit the frameworks that will be loaded.
selenium    | 11:33:33.592 INFO - Executing: [new session: Capabilities [{rotatable=false, nativeEvents=false, browserName=firefox, takesScreenshot=true, javascriptEnabled=true, version=, platform=ANY, cssSelectorsEnabled=true}]])
selenium    | 11:33:33.613 INFO - Creating a new session for Capabilities [{rotatable=false, nativeEvents=false, browserName=firefox, takesScreenshot=true, javascriptEnabled=true, version=, platform=ANY, cssSelectorsEnabled=true}]
selenium    | 11:33:37.954 INFO - Done: [new session: Capabilities [{rotatable=false, nativeEvents=false, browserName=firefox, takesScreenshot=true, javascriptEnabled=true, version=, platform=ANY, cssSelectorsEnabled=true}]]
selenium    | 11:33:37.966 INFO - Executing: [get: http://172.18.0.3:3000/])
selenium    | 11:33:39.078 INFO - Done: [get: http://172.18.0.3:3000/]
selenium    | 11:33:39.105 INFO - Executing: [find elements: By.xpath: /html])
selenium    | 11:33:39.289 INFO - Done: [find elements: By.xpath: /html]
selenium    | 11:33:39.303 INFO - Executing: [is displayed: 0 [[FirefoxDriver: firefox on LINUX (178058bb-7190-472a-b65c-69b21bbdff3e)] -> xpath: /html]])
selenium    | 11:33:39.402 INFO - Done: [is displayed: 0 [[FirefoxDriver: firefox on LINUX (178058bb-7190-472a-b65c-69b21bbdff3e)] -> xpath: /html]]
selenium    | 11:33:39.410 INFO - Executing: [get text: 0 [[FirefoxDriver: firefox on LINUX (178058bb-7190-472a-b65c-69b21bbdff3e)] -> xpath: /html]])
selenium    | 11:33:39.452 INFO - Done: [get text: 0 [[FirefoxDriver: firefox on LINUX (178058bb-7190-472a-b65c-69b21bbdff3e)] -> xpath: /html]]
selenium    | 11:33:39.464 INFO - Executing: [delete all cookies])
selenium    | 11:33:39.485 INFO - Done: [delete all cookies]
selenium    | 11:33:39.494 INFO - Executing: [get: about:blank])
selenium    | 11:33:39.576 INFO - Done: [get: about:blank]
selenium    | 11:33:39.588 INFO - Executing: [find elements: By.xpath: /html/body/*])
selenium    | 11:33:39.617 INFO - Done: [find elements: By.xpath: /html/body/*]
test_app    | .
test_app    |
test_app    | Finished in 7.03 seconds (files took 13.39 seconds to load)
test_app    | 1 example, 0 failures
test_app    |
selenium    | 11:33:39.631 INFO - Executing: [delete session: 859dc787-21dc-4715-80f2-d0305f06bce3])
selenium    | 11:33:39.758 INFO - Done: [delete session: 859dc787-21dc-4715-80f2-d0305f06bce3]
test_app exited with code 0
```

# Conclusion

In this blog post I have presented how to run your Selenium tests in a Docker environment. For people new to Docker it may be quite hard to fit all the pieces together and I hope this will be helpful to some fellow engineer.

If you enjoyed this blog post you can also follow me on twitter. Looking forward to hearing your comments!

# References
