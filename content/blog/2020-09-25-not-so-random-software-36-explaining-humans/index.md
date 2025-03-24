---
title: "Not So Random Software #36 - Explaining Humans"
date: 2020-09-25
categories: 
  - "newsletter"
tags: 
  - "git"
  - "humans"
  - "ruby"
  - "science"
  - "webdevelopment"
---

Hello everyone and welcome back to Not So Random Software!

After a long summer break, I am back with the usual short collection of weekly links. I have been thinking a lot about how to challenge my thinking, how to force me to see other people's perspectives, and even more importantly how to coach other people to do the same. I hope some of these links might help you do just that.

Enjoy the random walk!

## One article or paper

Very short functions are a code smell

This article ambitiously tries to collect data to determine if there is any correlation between function size and the number of bugs in an open-source project. I might not be in agreement with the conclusion, but the data seems to suggest there is some level of correlation indeed, so be careful when you do these method extractions, make sure you have your unit tests.

## One video or podcast

GOTO 2020 • You Really Don't Need All That JavaScript, I Promise • Stuart Langridge

Stuart Langridge aims at both analyzing the rationale and then challenge some of the reasons why we have all that Javascript running in our browser nowadays. A great summary to help you think twice about the tradeoffs of that choice.

## One book

Explaining Humans: What Science Can Teach Us about Life, Love and Relationships

In her book, Dr Camilla Pang draws multiple connections between humans (and their strange behaviors) and science phenomenons like protein folding, law of thermodynamics, gradient descent, photonics, wave theory, Brownian motion, Heisenberg Uncertainty Principle, fuzzy logic, electromagnetism, and much more. I love analogies, and this book will give you plenty; a great companion for when you don't know what mental model to use to interpret our messy world, science might just have the answer.

## One tool

Learn Git Branching

If you have struggled with git in the past (who doesn't?) this web page offers a great hands-on tutorial from basic concepts to advance ones.

## One line of code

If you are trying to group your user by the day they got created you might have come up with something like this

```
User.order("DATE(created_at)").group("DATE(created_at)").count
```

or worse

```
User.all.group_by { |user| user.created_at.to_date }.map { |k, v| [k, v.count] }
```

️ If you do a ot of these, consider using https://github.com/ankane/groupdate, and you get this instead (❤️ Ruby)

```
User.group_by_day(:created_at).count
# {
#   Sat, 24 May 2020 => 50,
#   Sun, 25 May 2020 => 100,
#   Mon, 26 May 2020 => 34
# }
```

and you also get advanced options like

```
User.group_by_day(:created_at, range: 2.weeks.ago..Time.now).count
```

## One quote

> Better to turn up with a watermelon someone doesn't want than with nothing at all.
> 
> Camilla Pang - Explaining Humans

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
