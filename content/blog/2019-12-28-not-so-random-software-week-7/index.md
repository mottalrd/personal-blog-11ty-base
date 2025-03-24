---
title: "Not So Random Software #7 - Goal Setting"
date: 2019-12-28
categories: 
  - "newsletter"
tags: 
  - "goalsetting"
  - "ruby"
  - "strategy"
---

After last week's reflection time, this week is about goal setting for the new year. Over the years I have found hundreds of strategies for doing this type of exercise and it's easy to get lost; accept that it is a challenging problem to crack. For comparison, seemingly simple problems like the Traveling Salesman or the Knapsack problem are known to be so hard that the most powerful machine can't solve them in a reasonable time — what makes you think you can objectively define, or let alone solve your yearly goals? Just relax the problem. Focus on what you can control (the Stoics knew a thing or two about that) and remember that's it all about enjoying the up and downs; you can't have it all, life goes with periods of balance counterbalance moves. Which side you are going to swing this year? or quarter?

## A random article or paper

Goal setting will often bias you towards outcomes. But the _What_ is nothing without the _How_. As a leader and owner of your life outcomes it will always come down to you, and what you do on a daily basis to move that outcome.

This article by the blogger Sachin Rekhi describes the _Bill Walsh_ approach to training the San Francisco 49ers, three times Superbowl champions. Constantly define what excellence looks like in your daily roles, and focus on constantly raising the bar for each of your habits. If you do that, _the score will take care of itself._

## A random video or podcast

In this video, Tim Ferris describes how the Stoic's exercise of _Premeditatio Malorum_ helped him overcome some of the most challenging decisions of his life and by doing so transforming what seemed to be overcoming insurmountable walls into life-changing opportunities. That's his argument on _Why you should define your fears instead of your goals_.

## A random book

The book Good Strategy/Bad Strategy: The Difference and Why It Matters. highlights why defining the _What_ is nothing without the _How_. Pushing for ambitious goals does not help without a clear diagnosis of what problem we are trying to solve and what tactics we are going to deploy to effectively tackle our challenge.

## A random tool

You Are Your Own Gym helped me stop making excuses for not exercising every day. It has a huge library of exercises that you can do at home with nothing but your body, a table, and a door. You can follow the weekly program, or if you have just 10 minutes the apps will generate a workout for the time you have available. Really, you have no excuses anymore.

## A random line of code

Ruby 2.7 is out, so I can't avoid showcasing one of the most interesting new features, _Pattern Matching_. Credit for the example to this article where you can find more details.

```
class PatternRouter
  def self.call(env)
    # pattern matching works only for symbols now
    # we need to symbolize keys first
    symbolized_env = env.inject({}){|memo,(k,v)| memo[k.to_sym] = v; memo}

    case symbolized_env
    in {REQUEST_METHOD: "GET", QUERY_STRING: ""}
      [200, {}, ["empty query string"]]
    in {REQUEST_METHOD: "GET", QUERY_STRING: params}
      [200, {}, ["query string: #{params}"]]
    in {REQUEST_METHOD: method}
      [405, {}, ["unsupported method: #{method}"]]
    else
      [400, {}, ["no request method provided"]]
    end
  end
end
```

## A random quote

> Hard choices, easy life. Easy choices, hard life.
> 
> Jerzy Gregorek

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
