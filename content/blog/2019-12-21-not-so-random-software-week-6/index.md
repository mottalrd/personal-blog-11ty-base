---
title: "Not So Random Software #6 - Reflection"
date: 2019-12-21
categories: 
  - "newsletter"
tags: 
  - "bugs"
  - "debugging"
  - "encoding"
  - "reflection"
  - "ruby"
---

Another year has gone by. Days, weeks and months disappear in the blink of an eye. We are busier than ever, and if you happen to live in London you know what I am talking about. We feel the pressure to deliver more and more, but we are rarely encouraged to stop and reflect on why we do what we do. Well, finally now it is time to take a break.

## A random tool

Ruby critic is a gem that wraps around static analysis gems such as Reek, Flay and Flog to provide a quality report of your Ruby code.

## A random line of code

Next time you are trying to write a £ symbol into a CSV using Ruby, keep in mind that it defaults to UTF-8, but Excel does not read it back correctly by guessing a different encoding. Simple solution, switch encoding like this.

```
CSV.open(filename, 'w:ISO-8859-1') do |csv|
  csv << ['Payment 1', '£ 15']
  csv << ['Payment 2', '£ 10']
end
```

## A random video or podcast

In this video Bryan Cantrill explores the importance of leadership principles ranging from the Gettysburg Address by Abraham Lincoln to Uber. Hilarious but also extremely serious; something we should all spent considerably more time thinking about.

## A random article or paper

The best way to learn is to avoid the natural tendency to ignore your mistakes, and instead, constantly reflect on what you should do differently. A practical example? Donald Knuth logged more than 800 errors he made while writing TeX in this paper that appeared in the Journal of Software in 1989.

## A random book

Sometimes the first reaction, when someone tells you could have done something better, is to defend yourself, build excuses and shy away. But the hard truth is that It's All Your Fault (Farnan Street blog). The book Thanks for the Feedback helped me see these moments like a great opportunity that I should be grateful for. Be worried when no one is telling you what you can improve.

## A random quote

> The road to wisdom?  
> \-- Well, it's plain and simple to express:  
> Err  
> and err  
> and err again  
> but less  
> and less  
> and less.
> 
> Piet Hein

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
