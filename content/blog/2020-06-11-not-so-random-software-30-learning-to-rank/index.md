---
title: "Not So Random Software #30 - Learning to rank"
date: 2020-06-11
categories: 
  - "newsletter"
tags: 
  - "machinelearning"
  - "neuralnetworks"
  - "ranking"
  - "ruby"
---

Hello everyone and welcome back to Not So Random Software!

It's been a while since I blogged about neural networks and how to use them to rank a set of items based on the users' preferences. The blog was in 2015 and a lot has happened since then. I think it might be a good time to recap some of the resources that I stumbled upon over this period.

Hope you enjoy this random selection of links!

## A random article or paper

Applying deep learning to Airbnb search

When I started looking at pairwise ranking in this article a few years ago the community was quite young. I was very pleased to see that in 2018 Airbnb published this article presenting their results using a real production dataset. The article does not only show the end result but also walks you through some of the failures they had along the journey. Inspirational!

## A random video or podcast

Learning from ranks, learning to rank - Jean-Philippe Vert, Google Brain

In this video published by the Alan Turing Institute, Jean-Philippe Vert from Google Brain presents his research on learning to rank. Lots of formulas ahead, but a very strong foundation if you want to understand how to properly formalize this machine learning problem.

## A random book

Neural Networks and Deep Learning, Springer

Because of COVID the Springer website made a number of very high-quality books available for free to download. If you didn't catch the opportunity now is the time to grab this book on Neural Networks and Deep Learning.

## A random tool

Ruby-fann gem for simple neural networks in Ruby

RubyFann, or "ruby-fann" is a ruby gem that binds to FANN (Fast Artificial Neural Network) from within a ruby/rails environment. FANN is a free (native) open-source neural network library, which implements multilayer artificial neural networks, supporting both fully-connected and sparsely-connected networks. It is easy to use, versatile, well documented, and fast. RubyFann makes working with neural networks a breeze using ruby, with the added benefit that most of the heavy lifting is done natively.

## A random line of code

Ruby-fann is a set of bindings to the native library written in C. The API is super simple to start with, literally 5 lines of code!

```
require 'ruby-fann'
train = RubyFann::TrainData.new(:inputs=>[[0.3, 0.4, 0.5], [0.1, 0.2, 0.3]], :desired_outputs=>[[0.7], [0.8]])
fann = RubyFann::Standard.new(:num_inputs=>3, :hidden_neurons=>[2, 8, 4, 3, 4], :num_outputs=>1)
fann.train_on_data(train, 1000, 10, 0.1) # 1000 max_epochs, 10 errors between reports and 0.1 desired MSE (mean-squared-error)
outputs = fann.run([0.3, 0.2, 0.4])
```

## A random quote

> If you can't explain it to a six year old, you don't understand it yourself.
> 
> Albert Einstein

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
