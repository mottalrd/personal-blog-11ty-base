---
title: "Not So Random Software #21 - Technical debt"
date: 2020-04-08
categories: 
  - "newsletter"
tags: 
  - "effectiveteams"
  - "softwaredesign"
  - "techdebt"
---

Hello there! This week I am thinking about technical debt; an incredibly overloaded term in our industry that requires to be untangled to really use it for decision making. How many types of technical debts are out there? How do we compare the risk/value of working on such debt versus other features? In what ways technical debt is linked to the human element of building software? I am not sure I am able to answer all these questions, but join me on this random walk to find out more!

## A random article or paper

Towards an understanding of technical debt.

Kellan Elliott-McCrea is the former Etsy CTO and now works at Dropbox. In this article he presents 5 types of technical debt:  
  
(1) Maintenance work: the necessary ongoing maintenance work a codebase needs \[...\] a shorthand for buying a breathing room.  
  
(2) Features of the codebase that resist change: Examples include poor (or too much) modularization, poor (or too much) documentation or poor (or inappropriate) test coverage.  
  
(3) Operability choices that resist change: Examples include unreliable deployments, lack of essential monitoring, unreliable/flakey tests, extensive coordination for releases, lack of staging environments.  
  
(4) Code choices that suck the will to live: We don’t understand the code, and when we don’t understand things, as humans, we tend to get scared, tired, and angry. Often we find this pattern in teams who’ve inherited a codebase.  
  
(5) Dependencies that resist upgrading: Technical decisions that bind a codebase to a technology that due to the passage of time has become a liability: it has stopped receiving updates, expertise is _difficult to find, upgrade paths become convoluted._

## A random video or podcast

A Crystal Ball to Prioritize Technical Debt

Adam Tornhill is the author of Your Code as a Crime Scene from the Pragmatic Bookshelf. In his talk at the InfoQ conference, he presents a set of data-driven methodologies to identify tech debt supported by real codebase examples; super interesting!

## A random book

Working Effectively with Legacy Code.

Michael Feathers mentored hundreds of developers, technical managers, and testers on how to bring their legacy systems under control. This book offers start-to-finish strategies for working more effectively with large, untested legacy code bases.

## A random tool

Codealong

If you can't afford Gitprime to get visibility into your coding processes, there is a good enough open-source alternative! This is not about measuring people's performance, but to get a feeling of which areas of your codebase you are paying tech debt interest on; slower than usual development might be an indicator of tech debt.

Another alternative which is more code-centric is Adam Tornhil tool mentioned in his talk called code-maat. The main takeaway there for me is to identify hotspots in the codebase and logical coupling between components; hotspots are necessarily places of high tech debt interest, logical coupling might suggest a refactoring to pay down the interest.

## A random line of code

People that never went beyond basic VIM commands might not have realized that what appears to be simple hotkeys is actually an entire text editing programming language! Here is an example "snippet" that adds semicolumns to this code (credits to Vimgolf!)

```

 super.onCreate(savedInstanceState)
 setContentView(R.layout.activity_second)
 Intent intent = getIntent()
 String text = intent.getStringExtra("text")

 TextView view = findViewById(R.id.textView2)
 view.setText(text)
```

```
A;<Esc>j.j.j.jj.j.ZZ
```

or even better

```
:%s/$/;/g<CR>kkxZZ
```

## A random quote

> When you think of tech debt, don’t think only in terms of the business problem of delayed features and rising defect counts. Think of the human cost, and the much more serious, much longer term business problem that results.
> 
> Erik Dietrich

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
