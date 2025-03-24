---
title: "Not So Random Software #23 - Prototyping"
date: 2020-04-21
categories: 
  - "newsletter"
tags: 
  - "nocode"
  - "prototyping"
---

Hello there and welcome back to Not So Random Software!

This week I am thinking about prototyping. The challenge I always had with prototyping is that on one end you want to think about the high-level choices (value proposition, UX) but on the other hand you also want to quickly (minutes) validate if these hypotheses make any sense when you actually play with them on a real working system. This is usually where the flow breaks as we have to spend usually hours (if not days) to wait for feedback about our high-level value proposition waiting for the _system_ to be implemented.

So here is the challenge; how can we keep the flow going while thinking both at a high level and quickly validating at a low level? Coding gives you the maximum freedom in terms of representing what you want but on the other end, you quickly get bogged down in the details. The paper helps you stay abstract and in the flow but doesn't tell you enough about how the product _feels_ when you use it because...well you haven't built one yet.

I have heard no-code tools made lots of progress lately, so I went ahead and researched some, here are some random links about what I found, hope you enjoy!

## A random article or paper

A review of 12 low code and no code development platforms

This article has a huge collection of no-code tools for all sorts of environments, from the individual to the enterprise. I have only tried a couple but it's definitely a source of inspiration to realize there is so much out there to get something up and running with very little code.

## A random video or podcast

Hammock Driven Development - Rich Hickey

Sometimes if you are stuck and you can't get in the flow, you might just need more nap time. In this talk Rich Hickey — the creator of Clojure — presents the challenges of thinking about complex systems and how he approaches this problem by...sleeping on it!

## A random book

Shape Up.

In this book, Ryan Singer presents the product building philosophy at Basecamp and in the context of prototyping, I found the chapter on shaping projects quite enlightening. Here they present a typical session of how creating a TODO list interface looks like at the shaping stage and how far you should go before pitching it to the team for prioritization and implementation. TLDR; you need to mitigate the long tail of risk that would result in a failed or over-budget project.

## A random tool

Bubble and Pakyow

Two tools today because...why not!

Bubble is a commercial no-code tool and I found it quite interesting. Sure you quickly stumble upon limitations about the fact you can't run loops and such, but you can get pretty far with the existing computation model.

Pakyow is a design-first web framework, meaning it uses reflection on frontend markup to automagically create backend routes and persistence. The authors claim you can extend what has been generated for you, I find it quite puzzling, but still seems an amazing piece of technology.

## A random line of code

Did you know that you can quickly embed an image in HTML using a base64 encoded version? Well...now you do!

```

```

or using CSS

```

li {
  background:
    url(data:image/gif;base64,R0lGODlhEAAQAMQAAORHHOVSKudfOulrSOp3WOyDZu6QdvCchPGolfO0o/XBs/fNwfjZ0frl3/zy7////wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACH5BAkAABAALAAAAAAQABAAAAVVICSOZGlCQAosJ6mu7fiyZeKqNKToQGDsM8hBADgUXoGAiqhSvp5QAnQKGIgUhwFUYLCVDFCrKUE1lBavAViFIDlTImbKC5Gm2hB0SlBCBMQiB0UjIQA7)
    no-repeat
    left center;
  padding: 5px 0 5px 25px;
}
```

## A random quote

> People often talk about “cutting” scope. We use an even stronger word — hammering — to reflect the power and force it takes to repeatedly bang the scope so it fits in the time box.
> 
> Ryan Singer, Shape Up

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
