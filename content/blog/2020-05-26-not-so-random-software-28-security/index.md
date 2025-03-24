---
title: "Not So Random Software #28 - Security"
date: 2020-05-26
categories: 
  - "newsletter"
tags: 
  - "agile"
  - "cyber-security"
  - "ruby"
  - "security"
---

Hello everyone and welcome back to Not So Random Software!

When we talk about software development we bake quality into the process by writing tests, and doing code reviews on a daily basis. Why security should be any different? Without security, users can't trust what we build and the digital world we create is only a shadow of what it could be. Unfortunately it is often easier said than done. Prioritizing security efforts is a much bigger challenge compared to prioritizing features because of the difficulty in estimating the business value of such work. It deserves a random walk.

Hope you enjoy this random selection of links!

## A random article or paper

Agile threat modeling

Threat modeling is often considered a vague and difficult exercise. In this blog post in Martin Fowler's blog author Jim Gumbley walks us through a simple agile approach to security threat modeling.

## A random video or podcast

Steve Jobs lecture at MIT

In this video Steve Jobs is talking to MIT students about his vision for NEXT. I was particularly impressed by how highly he was talking about object-oriented programming and the vision that developers would build applications out of components in the future. Something that never quite became true in my opinion; the no silver bullet conjecture of Fred Brooks seems to hold.

## A random book

The Web Application Hacker's Handbook

I have been recommended this book several times as the reference text for web application security. This together with a good read to the OWASP top 10 should get you covered against the most common attacks and beyond.

## A random tool

Metasploit _/_ Detectify / App check

Three automated security scanners I came across recently. They live at different ends of the price spectrum (roughly USD 300/month on Appcheck, USD 50/month on Detectify, and free for Metasploit). I am currently trying both to see what vulnerabilities they are able to uncover and how the information is presented to the user; definitely a fascinating world. Obviously I can't resist mentioning that Metasploit is written in Ruby!

## A random line of code

If you are building a React application running on localhost:8000 and a backend application running on localhost:3000 the browser will stop your requests because of the CORS policy. The solution is to configure your webpack dev server to proxy your requests to the backend and remove the browser from the equation.

```
module.exports = {
  //...
  devServer: {
    proxy: {
      '/api': {
        target: 'http://localhost:3000',
        pathRewrite: {'^/api' : ''}
      }
    }
  }
};
```

## A random quote

> For many organizations, security comes down to basic economics. If the cost of security is less than the likely cost of losses due to lack of security, security wins. If the cost of security is more than the likely cost of losses, accept the losses.
> 
> Bruce Schneier

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
