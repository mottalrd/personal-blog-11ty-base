---
title: "Not So Random Software #48 - The Stop Experiment"
date: 2021-08-03
categories: 
  - "newsletter"
tags: 
  - "organizationdesign"
  - "softwarearchitecture"
  - "softwaredesign"
  - "systemthinking"
---

Hello everyone and welcome back to Not So Random Software!

The last few months I have learned the hard way that if you want to think clearly, you need to _slow down_. Because nothing in life is as important as you think it is, while you are thinking about it. You develop a blind spot, which made me appreciate the value of a _Stop Experiment._

Let me explain, my recipe for building up motivation is quite simple. I write my expectations and goals for the week, or for the year, and then I remind myself to look at them constantly every single week. I build a framing narrative that pulls me into the future. This can be really effective for your growth and personal development.

So what's the blindspot? You get so good at using time, that you end up forgetting about _living_ the time you have. You think about the year ahead, but you forget about the decades where friendship, love, and family happen. You eat many delicious meals, but you forget to savor them.

The _Stop Experiment_ will help you see your blindspot. Stopping is a perfectly valid scientific experiment, but for hard-working people, it might not feel like one. So if you see this newsletter space empty for some time, I am probably testing out a hypothesis.

Enjoy the random walk!

## One book

How to Be a Stoic: Using Ancient Philosophy to Live a Modern Life

I have been enjoying reading this book and in the context of stepping out of the treadmill, it was a good reminder to think about the Stoic virtues of wisdom, courage, temperance, and justice. In a society where hyper competition is all we think about, it's good to step back and see how we can think about living a _good life_. But don't be fooled by another formula. You cannot achieve peace and happiness directly or even work toward it. Rather, you can only work toward understanding (Naval). By understanding, you will naturally become a more peaceful and happy person.

## One article or paper

Happyness - Naval

This is both a podcast and a write-up on happiness by Naval Ravikant. He covers many philosophical topics on how to better understand happiness and our relation to it. It's a long read but one that is worth revisiting many times. One that did stick with me recently is that Our environment rewards pessimism and paranoia. Modern society is safe and peaceful. Yet, we work and live every day like if we are not able to get food for our family tonight. Yet most of us in the Western world do

Modern society’s a lot safer and more peaceful. It still makes sense to be careful, maintain some paranoia, and occasionally to get angry—but not as much as we’re hardwired to do. It’s okay to dial it down. Our evolved nature rewards pessimism. But we live in much safer times, so we must find ways past that and work towards peace.

## One video or podcast

Daniel Kahneman: Putting Your Intuition on Ice

In this podcast Psychologist and Nobel laureate Daniel Kahneman talks about the actions we can take to overcome our biases. My favorite insight is that very quickly we form an impression and then we spend most of our time confirming it instead of collecting evidence. For most things, as an individual is very unlikely you can prove some universal truth of what works and what doesn't. Context is more important than you think, and you need to constantly update your view to match the situation at hand.

## One tool

Moleskine Smart Writing Set

I have been using this notebook for over a year now and I highly recommend it. Using a paper notebook is helpful to separate between the journaling (paper) and the work (screens). The smartpen coupled with a phone app makes your notes available immediately in digital form for later retrieval. I have already used over 10 notebooks this year, roughly one each month; over time the digital solution is the only way if I ever want to go back to them.

## One snippet of code

Git can be wonderful, and I believe people massively underestimate the amount of information they can gather by digging into commits history. In this example, I was looking for all the ab\_tests we did under the app/domain\_services folder in my app. They might not be there at current, but I wanted to find the usage we did in the past. This line built on top of git-grep made the magic!

```
git grep ab_test $(git rev-list --all -- app/domain_services) -- app/domain_services
```

But how does this actually work? First we get all the commits that affected app/domain\_services

```
git rev-list --all -- app/domain_services
```

This produces a list like this one, not very helpful

```
aaaf08f026f6138d2e94a25baa6172b001296496
a4c97bb475c11d5b689a58073a3795e16db19543
31757af75dca9f1c6043d686b5b84c8b79d5162d
e41f3f72f9e3e40a684fab630e642647c55ed1cd
```

You can then use command substitution in Bash to generate a look in your one-liner. That's what the $() is doing. Now git-grep is going to look for ab\_test in each of these commits, as follows.

```
git grep ab_test aaaf08f026f6138d2e94a25baa6172b001296496
```

But if you are interested just in the app/domain\_services subfolder you need to be more specific.

```
git grep ab_test aaaf08f026f6138d2e94a25baa6172b001296496 -- app/domain_services
```

And voilà!

## One quote

> The "normal" state of mind of most human beings contains a strong element of what we might call dysfunction or even madness. In Hinduism they call it Maya, the veil of delusion.
> 
> Eckhart Tolle

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
