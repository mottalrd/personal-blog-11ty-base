---
title: "Not So Random Software #38 - Is Technical debt just bullshit? And How to play the Piano"
date: 2020-10-06
categories: 
  - "newsletter"
tags: 
  - "javascript"
  - "learning"
  - "neuroscience"
  - "pianolessons"
  - "socialnetworks"
  - "techdebt"
---

Hello everyone and welcome back to Not So Random Software!

This week I have enjoyed reading this article commenting on technical debt and why today is used as a catch-all term for all types of dysfunctions. I have been recently experimenting on a system to objectively define and measure tech debt with teams and I hope to be sharing it soon; feel free to message me if you would like to hear more.

I am also starting a journey on how to play the Piano (Yamaha EZ 220) and found the Flowkey service to be really useful. Got told if I can type on VIM that well, I can definitely learn how to play the Piano. We will see if that hypothesis holds true in a few months.

Enjoy the random walk!

## One article or paper

Most Technical Debt Is Just Bullshit

_Because technical debt creates a bottleneck, it doesn't follow that every bottleneck is thus technical debt_. This is the argument that the author investigates by looking at the various definitions of technical debt by Martin Fowler, Uncle Bob, or Ward Cunningham. At the wikipedia page about technical debt, there is a long list of possible causes of technical debt.

- Insufficient up-front definition
- Lack of clear requirements before the start of development
- Lack of documentation
- Lack of a test suite
- Lack of collaboration / knowledge sharing
- Lack of knowledge/skills resulting in bad or suboptimal code
- Poor technical leadership
- Last minute specification changes

The author argues that these issues are called 'technical debt' because they can have a similar _outcome_ as technical debt. They can create a _bottleneck_. That's not helpful.

## One video or podcast

Making Sense - Welcome to the Cult factory - The Social dilemma

Sam Harris speaks with Tristan Harris, former Google's Design Ethicist and Product Philosopher, who studied how screen applications affect consumers in terms of their behaviour, patterns, connections, and overall health or attitude. Tristan is featured in the Netflix documentary "The Social Dilemma". They discuss the rise in teen depression and suicide, political polarization, conspiracy theories, information warfare, the decoupling of power and responsibility, the distinctions between platforms and publishers, and other topics.

## One book

How to take smart notes: : One Simple Technique to Boost Writing, Learning and Thinking – for Students, Academics and Nonfiction Book Writers

The Take Smart Notes principle is based on established psychological insight and draws from a tried and tested note-taking-technique. This is the first comprehensive guide and description of this system in English, and not only does it explain how it works, but also why. It suits students and academics in the social sciences and humanities, nonfiction writers and others who are in the business of reading, thinking and writing.

## One tool

Flowkey - Learn how to play piano online

The Flowkey app is able to recognize the note you play through the microphone and it guides you through your learning experience. I thought it was mind-blowing, there has never been an easier time in history to learn how to play a musical instrument.

## One line of code

I found this React cheatsheet this weekend which might come handy when experimenting with this framework. The ternary operator in React JSX templates makes my eyes bleed...is it just me?

```
// we can improve the logic in the previous example
// if isAuthenticated is true, how do we display both AuthLinks and Greeting?
function Header() {
  const isAuthenticated = checkAuth();

  return (
    <nav>
      <Logo />
      {/* we can render both components with a fragment */}
      {/* fragments are very concise: <> </> */}
      {isAuthenticated ? (
        <>
          <AuthLinks />
          <Greeting />
        </>
      ) : (
        <Login />
      )}
    </nav>
  );
}
```

## One quote

> “There are only two industries that call their customers 'users': illegal drugs and software.”
> 
> The Social Dilemma - Netflix

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
