---
title: "Not So Random Software #34 - Risk, the strategy game"
date: 2020-07-17
categories: 
  - "newsletter"
tags: 
  - "csv"
  - "excel"
  - "risk"
  - "ruby"
  - "strategy"
  - "utf-8"
  - "webpack"
---

Hello everyone and welcome back to Not So Random Software!

I have been enjoying the summer time in UK lately and with lockdown looking for more hobbies that I can do at home. One of them has been going back to Risk, one of the most famous strategy games of all time! And with that also how I would go about building a bot for it, but that's a topic for a longer blog post that I will eventually write.

Enjoy the random walk!

## One article or paper

Risk FAQ - University of Kent

For many years Owen Lyne at the Institute of Mathematics, Statistics and Actuarial Science of the University of Kent has maintained this list of FAQs about the game of Risk including the several variants in the different countries. Fun fact, I am obviously used to the Italian version where the defense has a stronger advantage; the defendant can play up to 3 dices, while in most other versions it can only play up to 2. I believe it makes it a completely different game!

## One video or podcast

RailsConf 2020 CE - Webpacker, It-Just-Works, But How? by Justin Gordon

Many experienced Rails developers find Webpack incredibly mysterious, and I agree. This talk from RailsConf 2020 (couch edition) will help you understand the internals of how Webpack works and how it is integrated into the Rails ecosystem; enlightening!

## One book

Total Diplomacy: The Art of Winning Risk

You might think that it's just a game, but once you start digging into this game, there is a lot more to it. With _Total Diplomacy: The Art of Winning Risk_ you will go beyond playing Risk or the use of strategy in games. You will explore how to understand a player's psychology, how to debate with people and influence them, when it is wise to break a deal or an alliance, and how to control your emotions and exploit others' weaknesses! An engaging read.

## One tool

VIA: Keyboard configuration tool

A few weeks ago we talked about QMK and how to configure your mechanical keyboard keys to fit your unique typing needs. VIA is built on top of QMK to make this process even easier! No more need to mess around with source C files to define your layout.

## One line of code

CSV is meant to be a simple format, but when Excel does add extra hidden bytes (called BOM, byte order mark) at the beginning of your file, that might generate errors when interacting with software that does not support such prefix. In those scenarios, here is how you can clean your CSV!

```
# Remove BOM for UTF-8 encoding
csv_entries = CSV.parse(list_body, headers: true).entries
headers = csv_entries.first.headers.map(&:dup)
bom_free_headers = headers.map { |field| field.force_encoding('UTF-8').remove("\xEF\xBB\xBF") }
```

## One quote

> Everything simple is false. Everything which is complex is unusable.
> 
> Paul Valéry

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
