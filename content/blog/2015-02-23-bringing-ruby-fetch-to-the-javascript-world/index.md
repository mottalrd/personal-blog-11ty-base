---
title: "Bringing Ruby fetch to the Javascript world"
date: 2015-02-23
categories: 
  - "article"
tags: 
  - "javascript"
  - "ruby"
  - "underscorejs"
  - "webdevelopment"
---

If you are a Rubyist you are probably comfortable using the _fetch_ method on a day-to-day basis but when you are developing in Javascript this sweetness is not immediately available. This is why I wrote underscorejs-fetch.

<!--more-->

The gist of the fetch method in Ruby is the following:

```
item = { name: 'pen', color: 'blue' }
item.fetch(:name)                                     #=> 'pen'

item.fetch(:price)                                    #=> key not found error
item.fetch(:price, '2

I wished I could find exactly the same in UnderscoreJS but _.has(), _.findKey() or _.property() are not quite what I am looking for.

So I went ahead and I implemented it myself. Here is how it works. If you have  an object and you want to fetch an existing property, you simply get it:

var item = { name: 'pen', color: 'blue' };
_.fetch(item, 'name'); //=> pen
On the other hand if the property is not available, you get an Attribute not found error in return:
var item = { name: 'pen', color: 'blue' };
_.fetch(item, 'price'); //=> Error('Attribute not found');

Now the sweetest part of fetch. When the property you are asking can't be found, you can simply pass a default:
var item = { name: 'pen', color: 'blue' };
_.fetch(item, 'price', '2

Finally -- for sophisticated people -- you also have the option to pass a callback in case the key you are looking for is not found:

var item = { name: 'pen', color: 'blue' };
_.fetch(item, 'price', function(key) { 
  return "The " + key + " cannot be found"; 
});
//=> 'The price cannot be found'
These example are also available as Jasmine specs in the Github repository. Running the specs is super-easy, just checkout the repository and run:
sudo npm install -g grunt-cli
npm install
grunt jasmine
There is no reason to publish a 33 lines method function apart from sharing it and having the opportunity to discuss it with the community.

You love fetch? Then go fetch the repo on Github and tell me what you think!

)                              #=> '2I wished I could find exactly the same in UnderscoreJS but _.has(), _.findKey() or _.property() are not quite what I am looking for.

So I went ahead and I implemented it myself. Here is how it works. If you have  an object and you want to fetch an existing property, you simply get it:

On the other hand if the property is not available, you get an Attribute not found error in return:

Now the sweetest part of fetch. When the property you are asking can't be found, you can simply pass a default:

Finally -- for sophisticated people -- you also have the option to pass a callback in case the key you are looking for is not found:

These example are also available as Jasmine specs in the Github repository. Running the specs is super-easy, just checkout the repository and run:

There is no reason to publish a 33 lines method function apart from sharing it and having the opportunity to discuss it with the community.

You love fetch? Then go fetch the repo on Github and tell me what you think!

item.fetch(:price) { |key| "the #{key.to_s} is 2$"}   #=> "the price is 2$"
I wished I could find exactly the same in UnderscoreJS but _.has(), _.findKey() or _.property() are not quite what I am looking for.

So I went ahead and I implemented it myself. Here is how it works. If you have  an object and you want to fetch an existing property, you simply get it:

On the other hand if the property is not available, you get an Attribute not found error in return:

Now the sweetest part of fetch. When the property you are asking can't be found, you can simply pass a default:

Finally -- for sophisticated people -- you also have the option to pass a callback in case the key you are looking for is not found:

These example are also available as Jasmine specs in the Github repository. Running the specs is super-easy, just checkout the repository and run:

There is no reason to publish a 33 lines method function apart from sharing it and having the opportunity to discuss it with the community.

You love fetch? Then go fetch the repo on Github and tell me what you think!
); //=> '2

Finally -- for sophisticated people -- you also have the option to pass a callback in case the key you are looking for is not found:

These example are also available as Jasmine specs in the Github repository. Running the specs is super-easy, just checkout the repository and run:

There is no reason to publish a 33 lines method function apart from sharing it and having the opportunity to discuss it with the community.

You love fetch? Then go fetch the repo on Github and tell me what you think!
)                              #=> '2

I wished I could find exactly the same in UnderscoreJS but _.has(), _.findKey() or _.property() are not quite what I am looking for.

So I went ahead and I implemented it myself. Here is how it works. If you have  an object and you want to fetch an existing property, you simply get it:

On the other hand if the property is not available, you get an Attribute not found error in return:

Now the sweetest part of fetch. When the property you are asking can't be found, you can simply pass a default:

Finally -- for sophisticated people -- you also have the option to pass a callback in case the key you are looking for is not found:

These example are also available as Jasmine specs in the Github repository. Running the specs is super-easy, just checkout the repository and run:

There is no reason to publish a 33 lines method function apart from sharing it and having the opportunity to discuss it with the community.

You love fetch? Then go fetch the repo on Github and tell me what you think!

item.fetch(:price) { |key| "the #{key.to_s} is 2$"}   #=> "the price is 2$"
```

I wished I could find exactly the same in UnderscoreJS but \_.has(), \_.findKey() or \_.property() are not quite what I am looking for.

So I went ahead and I implemented it myself. Here is how it works. If you have  an object and you want to **fetch** an existing property, you simply get it:

On the other hand if the property is not available, you get an _Attribute not found_ error in return:

Now the sweetest part of _fetch_. When the property you are asking can't be found, you can simply pass a default:

Finally -- for sophisticated people -- you also have the option to pass a callback in case the key you are looking for is not found:

These example are also available as Jasmine specs in the Github repository. Running the specs is super-easy, just checkout the repository and run:

There is no reason to publish a 33 lines method function apart from sharing it and having the opportunity to discuss it with the community.

You love fetch? Then go fetch the repo on Github and tell me what you think!

Finally -- for sophisticated people -- you also have the option to pass a callback in case the key you are looking for is not found:

These example are also available as Jasmine specs in the Github repository. Running the specs is super-easy, just checkout the repository and run:

There is no reason to publish a 33 lines method function apart from sharing it and having the opportunity to discuss it with the community.

You love fetch? Then go fetch the repo on Github and tell me what you think! ) #=> '2

I wished I could find exactly the same in UnderscoreJS but \_.has(), \_.findKey() or \_.property() are not quite what I am looking for.

So I went ahead and I implemented it myself. Here is how it works. If you have  an object and you want to **fetch** an existing property, you simply get it:

On the other hand if the property is not available, you get an _Attribute not found_ error in return:

Now the sweetest part of _fetch_. When the property you are asking can't be found, you can simply pass a default:

Finally -- for sophisticated people -- you also have the option to pass a callback in case the key you are looking for is not found:

These example are also available as Jasmine specs in the Github repository. Running the specs is super-easy, just checkout the repository and run:

There is no reason to publish a 33 lines method function apart from sharing it and having the opportunity to discuss it with the community.

You love fetch? Then go fetch the repo on Github and tell me what you think!

item.fetch(:price) { |key| "the #{key.to\_s} is 2$"} #=> "the price is 2$"I wished I could find exactly the same in UnderscoreJS but \_.has(), \_.findKey() or \_.property() are not quite what I am looking for.

So I went ahead and I implemented it myself. Here is how it works. If you have  an object and you want to **fetch** an existing property, you simply get it:

On the other hand if the property is not available, you get an _Attribute not found_ error in return:

Now the sweetest part of _fetch_. When the property you are asking can't be found, you can simply pass a default:

Finally -- for sophisticated people -- you also have the option to pass a callback in case the key you are looking for is not found:

These example are also available as Jasmine specs in the Github repository. Running the specs is super-easy, just checkout the repository and run:

There is no reason to publish a 33 lines method function apart from sharing it and having the opportunity to discuss it with the community.

You love fetch? Then go fetch the repo on Github and tell me what you think!
