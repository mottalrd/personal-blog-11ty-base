---
title: "Not So Random Software #16 - Leadership"
date: 2020-03-02
categories: 
  - "newsletter"
tags: 
  - "leadership"
  - "softwareengineering"
---

Welcome back to Not So Random Software, this week's links are dedicated to leadership. We often struggle to define it, measure it and promote it, but leadership is still a key factor for your tech team's success. This week's links serve as a good reminder of what to focus on. Enjoy this random walk!

## A random article or paper

6 Leadership styles and when you should use them

Not all people interpret leadership the same way, and that's why this article from Harvard Business Review is a good reminder of the different styles out there and when they are appropriate.

## A random video or podcast

Why good leaders make you feel safe

In this TED talk, Simon Sinek highlights why building a safe environment is key for leaders to be successful. Make your team feel safe, and they'll follow you.

## A random book

The Truth about Leadership: The No-Fads, Heart-Of-The-Matter Facts You Need to Know

Based on thirty years of research and more than one million survey responses, Kouzes and Posner highlight what they think are the 10 top traits that define a leader; lots of insights and practical examples. My favorite lately? _Values drive commitment_.

## A random tool

jrnl: A command-line journaling application

Being leadership so hard to measure and practice, I think journaling is one of the few tools that help you measure and challenge what you are doing every day; the second one is probably actively gathering feedback. There is a lot of choice for journaling tools out there, but this is all based on the command line, which some people might appreciate.

## A random line of code

A PostgreSQL LATERAL JOIN example.

Did you know that in PostgreSQL subqueries appearing in FROM clause can reference columns from preceding FROM items if you use the JOIN LATERAL keyboard? Well, now you do! Very useful to create funnel-like reports without the need for functions or ninja moves, best to play around with the DB-fiddle!

```
SELECT
  u.id,
  e1.event_type,
  e1.created_at,
  e2.event_type,
  e2.created_at,
  e3.event_type,
  e3.created_at
FROM
  users u,
  (
    SELECT
      event_type, created_at
    FROM events e1
    WHERE 
      e1.user_id = user_id and
      e1.event_type = 'visited_home_page'
  ) as e1
  LEFT JOIN LATERAL
  (
    SELECT
      event_type, created_at
    FROM events e2
    WHERE 
      e2.user_id = user_id and
      e2.event_type = 'clicked_product' and
      e2.created_at > e1.created_at
  ) as e2 on true
  LEFT JOIN LATERAL
  (
    SELECT
      event_type, created_at
    FROM events e3
    WHERE 
      e3.user_id = user_id and
      e3.event_type = 'paid_product' and
      e3.created_at > e2.created_at
  ) as e3 on true
```

## A random quote

> Leadership is the art of getting someone else to do something that you want done because he wants to do it, not because your position of power can compel him to do it, or your position of authority.
> 
> Dwight Eisenhower

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
