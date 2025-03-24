---
title: "Not So Random Software #29 - Waterfall history"
date: 2020-06-03
categories: 
  - "newsletter"
tags: 
  - "agile"
  - "automation"
  - "cloudworkflows"
  - "ruby"
  - "softwareengineering"
  - "waterfall"
---

Hello everyone and welcome back to Not So Random Software!

This week I am exploring the history of the Waterfall software development model to better understand how it came into place and the rationale behind it. In the era of Agile, we look at Waterfall as the evil from the past; I believe that by studying the historical context and the papers that influenced Waterfall we can better understand why we choose Agile today and how we can make software development better for the future.

Hope you enjoy this random selection of links!

## A random article or paper

Managing the Development of Large Software Systems

This paper from 1970 by Winston W. Royce is the first one who introduced the Waterfall model and explains it applicability. It's very interesting to see how the author did warn immediately that it's very hard to have a process that works in stages and that cycles are necessary, but most people at that time probably only read the first couple of pages!

A Spiral Model of Software Development

And since today we are talking about the history of Waterfall I can't omit this second paper where the Spiral Model has been developed as a response to the challenges of the early Waterfall adoption. It's funny how some of the sentences there to me actually closely resemble some of the Agile thinking; it talks about risks and iterative validation of your design.

## A random video or podcast

Back to Agile Basics, with Uncle Bob

In this podcast, Robert C. Martin (Uncle Bob) explains the history that led to the Agile movement, what role the Waterfall model played in this transition and the evolution of the Software Engineering profession.

## A random book

The Mythical Man Month

This book has been mentioned countless times and quoted for guidance on how to build software correctly. It's funny to me that this book was first published just 5 years after the Waterfall model has been presented by Winston Royce and even there there is a balanced mix of Agile thinking and Waterfall; Chapter 4 quotes that "conceptual integrity is the most important consideration in system design" suggesting that some sort of analysis and upfront architecture might be required, but at the same time Chapter 11 quotes "accept that fact of change as a way of life, rather than an untoward and annoying exception" therefore suggesting that we need to be ready to iterate over and over.

## A random tool

n8n.io - free and open source workflow automation too

If you are a Zapier user and you are considering building your own look no further; n8n.io is a framework to build your Zapier clone to automate your cloud workflows. Very cool.

## A random line of code

If you use memoization idiom in Ruby, remember that it doesn't work with booleans!

```
# wrong
@my_var =|| (a == b)

# correct
return @my_var if defined? @my_var
@my_var = (a == b)
```

## A random quote

> I believe in this (Waterfall) concept, but the implementation described above is risky and invites failure \[...\] The required design changes are likely to be so disruptive that the software requirements upon which the design is based and which provides the rationale for everything are violated. Either the requirements must be modified, or a substantial change in the design is required. In effect, the development process has returned to the origin and one can expect up to a 100-percent overrun in schedule and/or costs.
> 
> Winston Royce

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
