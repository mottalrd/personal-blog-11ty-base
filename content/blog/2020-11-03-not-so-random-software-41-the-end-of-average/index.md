---
title: "Not So Random Software #42 - The End of Average"
date: 2020-11-03
categories: 
  - "newsletter"
tags: 
  - "culture"
  - "diversity"
  - "statistics"
  - "timeseries"
  - "vim"
---

Hello everyone and welcome back to Not So Random Software!

This week I have been thinking about diversity and how to reconcile the problem of deviating from the expected norm when hiring in business. I am sold already; You don't need to convince me that diversity is a good thing to aim for. Said that I am also mindful that my actions alone will not be enough if I don't take into consideration the business environment I operate in, where risks and outcomes are the main variables to take into consideration; I can _easily_ justify my choice when a good looking CV doesn't work out, it's harder when a non-traditional CV doesn't go well. So how do I create a coherent, believable, and effective strategy to build a diverse, creative, smart and effective team without the constraints of traditional hiring methods? Can we embed experimenting with different profiles in the hiring process by taking a calculated risk in the expected business outcomes?

Enjoy the random walk!

## One article or paper

Inferring causal impact using Bayesian structural time-series models

Whenever you are trying to predict the effect of a marketing campaign or population and you can't AB test it, the traditional approach is to reach for a classic Difference-in-Differences scheme; those calculate the effect of a treatment on an outcome by simply comparing the average change over time in the outcome variable for the treatment group, compared to the average change over time for the control group. This Google Research paper demonstrates an alternative method based on state-space models. Such models make it possible to incorporate empirical priors on the parameters in a fully Bayesian treatment and accommodate multiple sources of variation, including the time-varying influence of contemporaneous covariates.

## One video or podcast

Discovering Culture through Artifacts

Mike McGarr, currently working in the Slack’s Frontend Infrastructure team, shares an approach to discovering organizational culture through its artifacts. Artifacts are not perfect; you can't draw hard conclusions from an artifact, but you get a hint. Examples of artifacts include Statement, Environment, Structure, Managers, Tools.

## One book

The End of Average: How We Succeed in a World That Values Sameness

This is the book that excited me the most this week and took a lot of my reading time. It really did speak to me. It highlights how our entire social system has been built around this average-size-fits-all model. Schools are designed for the average student. Healthcare is designed for the average patient. Employers try to fill average job descriptions with employees on an average career trajectory. The first half of the book is about explaining how this average-centric thinking came into place, the second half presents some strategies to tackle this problem.

## One tool

Rodauth: Ruby's Most Advanced Authentication Framework

Rodauth is an advanced authentication framework for Ruby. Compared to Devise it's less entangled with Rails and easier to configure to accommodate almost any conceivable authentication protocol!

## One line of code

VIM golf is an entertaining way to practice your skills by attempting to edit text with the lowest amount of keystrokes possible. I played one game this week and that was my solution.

```
qadt_$hxj0q@a@@@@@@:wq<CR>
```

to change this text

```
Assert.ThrowsAsync<Exception>(() => _auction.StartSellingItem());
Assert.ThrowsAsync<Exception>(() => _application.StartBiddingIn(_auction));
Assert.ThrowsAsync<Exception>(() => _auction.HasReceivedJoinRequestFromSniper());
Assert.ThrowsAsync<Exception>(() => _auction.AnnounceClosed());
Assert.ThrowsAsync<Exception>(() => _application.ShowsSniperHasLostAuction());
```

to this text

```
_auction.StartSellingItem();
_application.StartBiddingIn(_auction);
_auction.HasReceivedJoinRequestFromSniper();
_auction.AnnounceClosed();
_application.ShowsSniperHasLostAuction();
```

## One quote

> The expected value of your impact on the world is like a vector. It is defined by two things: direction and magnitude.
> 
> Sam Altman

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
