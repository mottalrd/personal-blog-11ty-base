---
title: "Not So Random Software #39 - Make it simple"
date: 2020-10-13
categories: 
  - "newsletter"
tags: 
  - "abstractions"
  - "authentication"
  - "complexity"
  - "jwt"
  - "ruby"
  - "systemdesign"
---

Hello everyone and welcome back to Not So Random Software!

This week I have enjoyed reading this article about complexity and how to think about it when building systems like web products. Couple it with this talk by Tom Stuart on how representations count, and you have the right tools to think about complexity.

Enjoy the random walk!

## One article or paper

Why Life Can't Be Simpler

> The total complexity of a system is a constant. If you make a user’s interaction with a system simpler, the complexity behind the scenes increases.
> 
> Lawrence Tesler (1945–2020)

In this article, the author presents how to think about complexity using the Energy analogy. When trying to make things simpler, we need to be aware that we are really shifting complexity around.

## One video or podcast

Representations count - Tom Stuart

In this talk, Tom Stuart explores how complicated code can get if you pick the wrong abstraction. Searching and looking for deeper insights on how we model our world can make a huge difference to the end result.

## One book

Managing the Design Factory

Being aware of complexity doesn't help if you don't know how to tackle it in the context of a team. There is nothing more complex than a group of humans collaborating on a hard problem. This book combines the powerful analytical tools of queuing, information, and system theories with the proven ideas of organization design and risk management. What you get is a methodical approach to consistently hit the "sweet spot" of quality, cost, and time in developing any product.

## One tool

Actionsflow - The free Zapier/IFTTT alternative for developers

Developers are getting excited about building their very own automation tool using Github's actions. I envy their effort, but personally I think for the price I would always go with a managed solution.

## One line of code

JSON Web Tokens are an open, industry-standard RFC 7519 method for representing claims securely between two parties. In Ruby, you can play around with the JWT gem like so:

```
require 'jwt'

payload = { data: 'test' }

# IMPORTANT: set nil as password parameter
token = JWT.encode payload, nil, 'none'

# eyJhbGciOiJub25lIn0.eyJkYXRhIjoidGVzdCJ9.
puts token

# Set password to nil and validation to false otherwise this won't work
decoded_token = JWT.decode token, nil, false

# Array
# [
#   {"data"=>"test"}, # payload
#   {"alg"=>"none"} # header
# ]
puts decoded_token
```

## One quote

> “When a thing looks complicated, it's possible that we are looking at it wrong and missing some of the pieces of the puzzle.”
> 
> Richard Feynman

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
