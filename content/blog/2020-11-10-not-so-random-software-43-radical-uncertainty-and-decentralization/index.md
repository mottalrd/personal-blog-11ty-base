---
title: "Not So Random Software #43 - Radical Uncertainty and Decentralization"
date: 2020-11-10
categories: 
  - "newsletter"
tags: 
  - "clojure"
  - "decentralizedsystems"
  - "decisionmaking"
  - "functionalprogramming"
  - "statistics"
---

Hello everyone and welcome back to Not So Random Software!

This week I have been thinking about decentralization, education, blockchain uses for finance products, and when not to use probabilities to solve your problems.

Enjoy the random walk!

## One article or paper

TechCrunch - Why The Internet Needs IPFS  
Wikipedia - The InterPlanetary File System

We have a fragile web still built on a centralised model that is fragile and forgetful. Based on the Internet Archive's own findings, the average webpage only lasts about 100 days. IPFS, is an open source project that taps into ideas pioneered by the decentralized digital currency Bitcoin and the peer-to-peer file sharing system BitTorrent. Sites opt in to IPFS, and the protocol distributes files among participating users. If the original web server goes down, the site will live on thanks to the backups running on other people's computers. What's more, these distributed archives will let people browse previous versions of the site, much the way you can browse old edits in Wikipedia or old versions of websites in the Wayback Machine

## One video or podcast

A Love Letter to Clojure

Gene Kim is one of the authors of the Phoneix Project and then followed with the Unicorn Project. In this talk he presents how the traits of Clojure and Datomic can be mapped to principles of systems that are linked to high performing happy teams:

- Locality and Simplicity
- Focus, Flow and Joy
- Improvement of Daily Work
- Psychological Safety
- Customer Focus

## One book

Radical Uncertainty : Decision-Making Beyond the Numbers

What do you do when probabilities aren't enough? Kay and King highlight the fallacies of statistical thinking for problems that are _wicked_ where there the rules of the game are not well defined and the processes that govern the data are non-stationary. A very good complement if you enjoyed the opposite view of How to Measure Anything.

## One tool

ChainLink: smart contracts connected to real world events

The Chainlink network provides reliable tamper-proof inputs and outputs for complex smart contracts on any blockchain. I haven't played yet with any blockchain technology, but that would be something I would be very happy to experiment with.

## One line of code

Sometimes a Hello World is worth a thousand words to get the initial feeling of a programming language, here is the one for Clojure

```
(ns clojure.examples.hello
   (:gen-class))
(defn hello-world []
   (println "Hello World"))
(hello-world)
```

And this is how a page looks like in the open source project memory-hole (a support issue organizer).

```
(defn home-page []
  (r/with-let [tags     (subscribe [:visible-tags])
               issues   (subscribe [:visible-issues])
               selected (subscribe [:selected-tag])]
    [:div.container
     [admin-groups-toggle]
     [:div.row
      [:div.col-sm-3
       [tags-panel @tags @selected]]
      [:div.col-sm-9
       [:h2 "Issues "
        [filters @selected]
        [new-issue]]
       [issue-search]
       (for [issue-summary @issues]
         ^{:key (:support-issue-id issue-summary)}
         [issue-panel issue-summary])]]]))
```

## One quote

> There is no general theory of how best to make decisions. Much of the academic literature on decision-making under uncertainty tries to frame the challenge as a puzzle. All decisions, it is assumed, can be expressed as mathematical problems. And potentially capable of being solved by computers. \[...\] Howerver humans have evolved to cope with problems which are not amenable to probabilistic reasoning \[...\] Our brains are not built like computers but as adaptive mechanisms for making connections and recognising patterns. Good decisions often result from leaps of the imagination. \[...\] Creativity is inseparable from uncertainty. By its nature, creativity cannot be formalised, only described after the event, with or without the help of equations.
> 
> King, Mervyn. Radical Uncertainty: Decision-making for an unknowable future

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
