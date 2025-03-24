---
title: "Not So Random Software #47 - Thinking in Systems"
date: 2021-03-24
categories: 
  - "newsletter"
tags: 
  - "organizationdesign"
  - "softwarearchitecture"
  - "softwaredesign"
  - "systemthinking"
---

Hello everyone and welcome back to Not So Random Software!

This week I have been thinking about teams; as someone who has to deal with computers every day it is easy to fall into the trap of applying software design principles to human people. Some elements do apply, but with humans the context and unique traits of each individual are everything, until they are not.

Enjoy the random walk!

## One book

An elegant puzzle

In this book Will Larson presents what he learned from scaling engineering organisations. I liked how he reduced the kernel of this hard topic to a few simple statements.

- The fundamental challenge of organizational design is sizing teams.
- The expected time to complete a new task approaches infinity as a team's utilization approaches 100%
- Hiring and training are often a team's biggest time investment

## One article or paper

Reframing the 8 causes of conflict

No matter how hard you work on organizational design, conflict is something you will always have to face. This article goes into the details of how to reframe these conflicts to you can handle them positively, but I keep this short list always front of my mind:

1. Conflicting resources.
2. Conflicting styles.
3. Conflicting perceptions.
4. Conflicting goals.
5. Conflicting pressures.
6. Conflicting roles.
7. Different personal values.
8. Unpredictable policies.

## One video or podcast

GOTO 2017 • DDD Today - Modeling Uncertainty • Vaughn Vernon

People often tell me that it is hard to deal with unplanned events constantly interrupting you. I think this sentence is contradictory on its own. If something unpredictable is always happening, then it is a predictable process. You just need to reframe it like that.

In this video Vaughn Vernon talks about some of the _unpredictable_ rare things that happen in distributed systems like out-or-order events and duplicated events. They are not unpredictable, they are happening all the time. Once you reframe it like that you can start building a protective infrastructure around them.

![](images/Screenshot-2021-03-24-at-08.03.26-300x225.png)

## One tool

Insight Maker

If you want some comfort and hope you can just abstract humans into a model, why don't you model them using Insight Maker? An Insight Maker's System Dynamic model reason in terms of _stock, flow, variable and links_. And there are some open source models too for you to learn! Here is one for Agile Project Management.

## One snippet of code

Did you know you can use a Poisson distribution generator in Ruby with the SciRuby package? Well now you do! Here is an example:

```
    it 'should return correct rng' do
      # The expected rng output when 1 is set as the seed value
      exp_means = [1, 2, 2, 3, 4, 5, 6, 7, 8, 9]

      lambda_val = rand(10) + 1
      exp_mean = exp_means[lambda_val - 1]
      seed = 1

      rng = @engine.rng(lambda_val, seed)

      samples = 100
      sum = 0
      samples.times do
        v = rng.call
        sum += v
      end
      mean = sum / samples
      expect(mean.to_i).to be_within(1e-10).of(exp_mean)
    end
```

## One quote

> A sick man only wants one thing, a healthy man wants 10,000 things.
> 
> Confucius

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
