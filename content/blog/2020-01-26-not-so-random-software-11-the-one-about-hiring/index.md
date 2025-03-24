---
title: "Not So Random Software #11 - Hiring"
date: 2020-01-26
categories: 
  - "newsletter"
tags: 
  - "hiring"
  - "productivity"
  - "ruby"
---

Welcome back to Not So Random Software. This week's links are dedicated to _Hiring_; how to navigate skills shortage landscape, reflections on what you actually need, and tools that might be helpful to get it done.

## A random article or paper

The First Round blog publishes wisdom from the top tech companies in Silicon Valley. This article collects some of the questions that people use to identify the right talent for their company.

## A random video or podcast

Some people say that your company culture is who you hire, fire, and promote. So take some time to reflect on what culture you actually want to build. In this podcast, Tim Ferris interviews Ben Horowitz, the author of What You Do Is Who You Are. I haven't read the book yet, but the conversation is interesting and helps you decode what _culture_ actually is.

## A random book

I never thought I would end up reading a book on hiring, but I guess there is a first time for everything. I am currently reading Who: The A Method for Hiring, but any other recommendation is welcome!

## A random tool

Hook is a tool to link and then retrieve associated files, email, web pages and more. Say for example you are currently working on hiring. You probably have three pieces of information in front of you; the HR tool, the candidate CV, and several web pages linked to that candidate. With Hook, you can keep your focus by linking all these items together with a shortcut and then jump back and forth between them. No more searching between the various windows or files!

## A random line of code

If you are trying to determine the date of the third Monday (or Tuesday, Wednesday, etc...) of a given month, you might realize that this is a bit more tricky than you initially guessed. The Ruby Way book actually has a snippet of code for that. I personally find it quite hard to read, but here it is!

```
def nth_wday(n, wday, month, year)
  if (!n.between? 1,5) or
      (!wday.between? 0,6) or
      (!month.between? 1,12)
    raise ArgumentError, "Invalid day or date"
  end
  t = Time.local year, month, 1
  first = t.wday
  if first == wday
    fwd = 1
  elsif first < wday
    fwd = wday - first + 1
  elsif first > wday
    fwd = (wday+7) - first + 1
  end
  target = fwd + (n-1)*7
  begin
    t2 = Time.local year, month, target
  rescue ArgumentError
    return nil
  end
  if t2.mday == target
    t2
  else
    nil
  end
end
```

## A random quote

> There are these two young fish swimming along and they happen to meet an older fish swimming the other way, who nods at them and says "Morning, boys. How's the water?" And the two young fish swim on for a bit, and then eventually one of them looks over at the other and goes "What the hell is water?
> 
> David Foster Wallace

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
