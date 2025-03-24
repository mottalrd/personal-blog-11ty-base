---
title: "Not So Random Software #45 - Be present, have a strategy"
date: 2021-02-05
categories: 
  - "newsletter"
tags: 
  - "essentialism"
  - "mindfulness"
  - "strategy"
---

Hello everyone and welcome back to Not So Random Software!

It has been a long break, with December and January being some of the hardest months on record for me. When the pressure was high I had to remember how to be present and quickly distinguish between the vital few and the trivial many.

Enjoy the random walk!

## One book

Essentialism: The Disciplined Pursuit of Less

Never like in the last two months the book Good Strategy Bad Strategy became a lifesaver for me. The realization that strategy is a complex narrative to help you distinguish between the vital few and the trivial many is an important one.

You can be efficient by staying organized and categorizing tasks like suggested in the Organized Mind or Getting Things Done. The second-order effect you don't see immediately is that you change the underlying system at pushing more tasks at you until you don't have the energy to handle them anymore.

So what do you do? You naturally try to be even more efficient; you look at the task types and work bottom-up to see the forest from the trees, but it doesn't work. You spend more time looking at the data than working on the data. You can't talk probability distributions when every event about you is so unique. You need a narrative to guide you through, as explained in Radical Uncertainty. Context is king in the complicated and uncertain life you live in, you need to set your direction.

Essentialism by Greg McKeown nicely completed this picture. With digital tools, pressure, and infinite tasks all around us we have lost control of our most precious resource; being there in the moment, fully present, and mentally sharp. If you are not dictating your day, or weeks anymore, it's time to step back and re-think about what really matters.

## One article or paper

Write five, then synthesize: good engineering strategy is boring.

In this blog post, Will Larson explains how to write a good strategy and vision for an Engineering organization, step by step.

## One video or podcast

Being Glue

In this video Tanya Reilly presents her story about getting busy with _glue work_ and finding herself in front of a hard career choice at the end.

## One tool

Pghero

A performance dashboard for PostgreSQL. When New Relic and similar are not enough to spot inefficient queries, this is a specialized tool to make your _explain analyze_ jobs a bit easier.

## One line of code

Using Rails in API only mode and making calls from a Javascript frontend could get quite painful if you don't know how to handle CORS. Cross-Origin Resource Sharing (CORS) is an HTTP-header based mechanism that allows a server to indicate any other origins than its own from which a browser should permit loading of resources. By default Rails doesn't allow you to make calls from different domains, the rack-cors gem has the solution for your local development. Handle with care in production!

```
class Application < Rails::Application
  config.middleware.insert_before 0, "Rack::Cors" do
    allow do
      origins '*'
      resource(
        '*',
        headers: :any,
        methods: [:get, :patch, :put, :delete, :post, :options]
      )
    end
  end
end
```

## One quote

> Courage is grace under pressure
> 
> Ernest Hemingway

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
