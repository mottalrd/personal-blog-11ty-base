---
title: "Not So Random Software #37 - Good Judgement and Static Typing"
date: 2020-09-29
categories: 
  - "newsletter"
tags: 
  - "judgment"
  - "learning"
  - "ruby"
  - "softwarearchitecture"
  - "statictyping"
---

Hello everyone and welcome back to Not So Random Software!

This week I am have been thinking about Judgement and what some simple exercises we can do every day to improve it. Stumbled upon a good article and a book in the process.

I also noticed in the Ruby community more people are talking about decoupling big applications by either thinking about Rails engines and components, or static type annotations in Ruby 3.

Enjoy the random walk!

## One article or paper

Notes on Good Judgement and How to Develop it

This article has a very good summary of exercises you can do every day to improve your judgment and why this is so important for your career. Here is a short list:

Train probabilistic reasoning  
Incentivize accuracy  
Think of alternatives  
Decompose the problem  
Combine multiple judgments

## One video or podcast

RailsConf 205 - Get started with Component Based applications

If you have ever struggled to get started with Rails engines and app components because it feels like an insurmountable challenge, this long workshop will help you with the first steps and dig into the hard details.

## One book

Pragmatic Thinking and Learning: Refactor Your Wetware

What happens if a programmer writes a book on how to improve your thinking? Andy Hunt is the co-author of The Pragmatic Programmer and Programming Ruby, and this book is about how to refactor your brain for lifelong learning.

## One tool

Packwerk - a Ruby gem used to enforce boundaries and modularize Rails applications

People at Shopify are releasing a ton of open source to help you deal with big applications. I have mixed feelings about this approach, but it's great to see the community pushing the boundaries of what's possible with Ruby!

## One line of code

Ruby 3 is shipping with RBS, a new way to write annotations and types, here is how it looks like! You can check for more details here https://github.com/ruby/rbs

```
module ChatApp
  VERSION: String

  class Channel
    attr_reader name: String
    attr_reader messages: Array[Message]
    # `|` means union types, `User` or `Bot`.
    attr_reader users: Array[User | Bot]

    def initialize: (String) -> void

    # Example of method overloading.
    def post: (String, from: User | Bot) -> Message   
            | (File, from: User | Bot) -> Message
  end
end
```

## One quote

> “errare humanum est, sed perseverare diabolicum: 'to err is human, but to persist (in the mistake) is diabolical.”
> 
> Lucius Annaeus Seneca

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
