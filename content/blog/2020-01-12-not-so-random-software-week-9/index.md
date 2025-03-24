---
title: "Not So Random Software #9 - Anger Management"
date: 2020-01-12
categories: 
  - "newsletter"
tags: 
  - "angermanagement"
  - "mindfulness"
  - "refactoring"
  - "ruby"
---

Welcome back to Not So Random Software. This week's links are dedicated to _Anger_ and our relation to it. As Seneca pointed out many years ago _we often suffer more in imagination than in reality_. Our response to feelings of anger make all the difference to what happens afterwards and our happiness.

## A random article or paper

In this article you can find a summary of the most common techniques on anger management from the ancients Stoics. Personally I find _focusing on what you can control versus what is out of your control_ one of the most useful and liberating ideas, followed by gretefulness.

## A random video or podcast

In this podcast leadership coach Jim Dethmer explains how to shift from the victim consciousness, where you’re defensive and attached to proving you’re right, to what he calls the creator consciousness, where you choose to be responsible for your own experience.

## A random book

In What We Really Do All Day insights from the Centre for Time Use Research are distilled to present us how really our days have changed since the 1960s. When I look at the time data it helps me detach from the problem of owning and controlling time; I shift my focus on what I can control, by choosing how I want to experience time rather then being a victim of it.

## A random tool

Last year the one purchase of £10 or less that really changed my life was getting an Electric Candle Lighter. I am more inclined to light up my candles at night and they help me relax and fall asleep.

## A random line of code

We project our lifes in software, and software is reflected back in the way we approach life. In this context Refactoring can be seen as a way to shift your perspecive on the world, by simplifying it a bit. Extracting methods is a surprisingly effective mechanism to do so. Here is a simple example.

Before:

```
class Invoice
  # ...

  def print
    print_branding

    # print line items
    line_items.each do |line_item|
      puts "#{line_item.name}: #{line_item.price}"
    end

    # print subtotal
    puts "Subtotal: #{line_items.sum(&:price)}"
  end
end
```

After

```
class Invoice
  # ...

  def print
    print_branding
    print_line_items
    print_subtotal
  end

  private

  def print_line_items
    line_items.each do |line_item|
      puts "#{line_item.name}: #{line_item.price}"
    end
  end

  def print_subtotal
    puts "Subtotal: #{line_items.sum(&:price)}"
  end
end
```

## A random quote

> Thoroughly unprepared, we take the step into the afternoon of life. Worse still, we take this step with the false presupposition that our truths and our ideals will serve us as hitherto. But we cannot live the afternoon of life according to the program of life's morning, for what was great in the morning will be little at evening and what in the morning was true, at evening will have become a lie.
> 
> Carl Gustav Jung

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
