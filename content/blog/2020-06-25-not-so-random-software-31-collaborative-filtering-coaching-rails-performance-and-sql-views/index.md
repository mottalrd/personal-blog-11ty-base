---
title: "Not So Random Software #31 - Collaborative Filtering, Coaching, Rails performance and SQL views"
date: 2020-06-25
categories: 
  - "newsletter"
tags: 
  - "coaching"
  - "collaborativefiltering"
  - "leadership"
  - "machinelearning"
  - "rails"
  - "ruby"
---

Hello everyone and welcome back to Not So Random Software!

This week links are as random as it gets; we will start with a research paper on collaborative filtering, will jump on a book on coaching, and close off with two Rails resources!

Hope you are not gonna get lost, enjoy the random walk!

## A random article or paper

Collaborative Filtering for Implicit Feedback Datasets

Five years ago I wrote about collaborative filtering in the context of holiday rentals recommendations. Today I would like to share this paper presented at the International Conference on Data Mining in 2008 by a team of researchers from AT&T Labs and Yahoo labs. The paper presents the concept of implicit feedback, i.e. what do you do when you lack substantial evidence on which products the consumer dislikes? Good question!

## A random video or podcast

Aaron Patterson talk at RailsConf 2020

In this video, Aaron Patterson (i.e. Tenderlove) presents what does it take to debug and solve a puzzling performance issue in Active Record. Very educational and also interesting to see how to unpack the magic of my web development framework.

## A random book

The Coaching Habit

According to this famous HBR article, we can recognize six different leadership styles; depending on the context of your company or your team you might want to get a leader that suits best or adapt your style to better serve your team. The styles are

- The pacesetting leader; would say “Do as I do, now.”
- The authoritative leader; would say “Come with me.”
- The affiliative leader; would say “People come first.”
- The coaching leader; would say “Try this.”
- The coercive leader; would say “Do what I tell you.”
- The democratic leader; would say “What do you think?”

I have spent a lot of deliberate practice using the coaching leadership style (has not been _always_ successful though!) and I found this book to be a great starting point if you want to give it a try.

## A random tool

Scenic gem

Active record can only go so far when you need to pull a dataset using a complex SQL statement; it is potentially slow, you need to look for n+1 problems and most importantly can become hard to read pretty quickly. Scenic is a gem that adds methods to ActiveRecord::Migration to create and manage database views in Rails. You can bring the power of SQL views to your Rails application without having to switch your schema format to SQL. Your view becomes like any other active record model! (read-only).

## A random line of code

Say you want to test something on your local machine, but you can't be bothered to use the interface of your app to create a complex test user, what do you do? Well, if you are using a gem like Factorybot to manage your test factories nothing is stopping you from loading Factorybot into a rails console and run your factory like you would in a test! Here is how:

```
require 'factory_bot'
FactoryBot.find_definitions
FactoryBot.create(:your_user_factory_name)
```

## A random quote

> One of the great commandments of science is, "Mistrust arguments from authority." … Too many such arguments have proved too painfully wrong. Authorities must prove their contentions like everybody else.
> 
> Carl Sagan

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
