---
title: "Not So Random Software #10 - Automation"
date: 2020-01-19
categories: 
  - "newsletter"
tags: 
  - "automation"
  - "ruby"
  - "softwareengineering"
  - "systemdesign"
---

Welcome back to Not So Random Software. This week's links are dedicated to _Automation_ and how we can keep a healthy relationship with it.

## A random article or paper

In an automated system two roles are left for the human operator; (a) monitoring that the automated system is working correctly, and (b) taking over control if it isn’t. Unfortunately operator’s skills decline over time — because of lack of continuous practice — and the situations that require human intervention are the ones the machine can't handle, by definition the most demanding ones. This article greatly summarize the paper Ironies of automation (Bainbridge, Automatica, Vol. 19, No. 6, 1983) where these challenges are described.

## A random video or podcast

_Easy_ choices are often the cause behind complex systems. To build _Simple_ systems — the ones you can understand and reason about — you need to be constantly fighting the urge to take the easy choice to unlock the design insights that will lead you to a simpler solution. This talk by Rich Hickey, the creator of Clojure, explains the tradeoff in great detail.

## A random book

In Shape Up, the author Ryan Singer describes how work is organized at Basecamp to take back control of Software development activities. One of my favourite hightlights is the work hill analogy where you separate the discovery phase from the execution phase. For that, a picture is worth a thousand words.

![A Hill Chart diagram. It looks like a wide bell curve, with a vertical dotted line down the middle. The far left edge is labeled: Start, and the far right edge labeled: Finish. The left slope going up is labeled: Figuring out what to do. The right slope going down is labeld: Getting it done. A dot is drawn about two-thirds of the way up the left side of the hill. Light-colored arrows suggest the dot originated at the left side, moved up to its current position, and later moves over the hill and down the right to the finish.](images/hill_concept-a0a77c0ebb209b61899b8b4cdb1a315f2807e3fdc2e1d2373e2f19060725f042.png)

## A random tool

Cooking; you either love it or hate it. When done with friend or loved ones on special occasions that's one of the most fulfilling things you can do in life. But the remaining 90% of daily routine meals...well I just don't find any value in it. I receive close to zero happiness as a result of my Wednesday work lunch meal. We might be far away from automating cooking, but this year I found Instant Pot. It is so good that feels like cheating.

## A random line of code

If you are working in Ruby and you want to execute some code around another piece of code — for example log statements — you might be tempted to do something like this;

```
def call
  puts "Start API call"
  APIClient.new.call
  puts "End API call"
end
```

If the surrouding code is complex enough to distract you from the main goal of the method, try this instead;

```
def call
  with_logging do
    APIClient.new.call
  end
end

def with_logging
  puts "Start API call"
  yield
  puts "End API call"
end
```

## A random quote

> Debugging is twice as hard as writing the code in the first place. Therefore, if you write the code as cleverly as possible, you are, by definition, not smart enough to debug it.
> 
> Kernighan’s Law

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
