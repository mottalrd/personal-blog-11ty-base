---
title: "Not So Random Software #26 - Searching Tools"
date: 2020-05-12
categories: 
  - "newsletter"
tags: 
  - "excel"
  - "javascript"
  - "unix"
  - "vim"
---

Hello there and welcome back to Not So Random Software!

This week I am thinking about tools and how they can deeply influence the way we think about problems in our daily life. Often a tool is all it takes to change something from impossible to straightforward; it completely changes the value equation. On the other hand, finding the right tool for the job is often surprisingly hard. As humans, we are full of biases and we have the tendency to either overcomplicate things or oversimplify them. In the quest for the right tool, we lose sight of what good enough looks like and what was the initial problem the tool was trying to tackle. I do not have any silver bullet for you I am afraid, but one principle worked for me so far; if you are having fun and you are learning along the way, it is not going to be time wasted, and irrespectively of the outcome you will walk away with happy memories of the experience.

I hope you enjoy this random selection of links!

## A random article or paper

Comparing Ember Octane and React

In this article, a core team member of Ember describes the differences between Ember and React for a small Hacker News clone. Going back to the famous No Silver Bullet paper by Frederick P. Brooks I have a hard time understanding how any of these differences might affect our capability to build applications considerably faster. The recent release of React Hooks makes the code more elegant in certain scenarios but at the cost of yet another decision that needs to be taken in terms of technical design. I am puzzled.

## A random video or podcast

You suck at Excel! By Joel Spolsky

Believe it or not for quite some time now I have been thinking about Excel and what a wonderful tool it is. I have been trying to deepen my knowledge from amateur to an expert via books and courses. If you think about it, most of what 80% of web developers do is replacing spreadsheet systems. If you think about it this way, you would think twice before overcomplicating your web solution. In this video Joel Spolsky shows a number of tricks you might not have heard of before; I am afraid yes, I do suck at Excel!

## A random book

UNIX Power Tools

Every time I come across some blog posts or articles on how to better use my everyday UNIX tools I find something that changes the way I work forever. For example, you might be surprised by how many people never tried Ctrl+R on the command line to quickly search through their history! This book gives you a structured and well-thought introduction to some of the most fundamental UNIX tools for your everyday development.

## A random tool

VIM dadbod - Run your SQL queries in VIM

Whenever I have to reach for the database I got used to UI tools like DBeaver but quite frankly sometimes it is overkill if all I have to do is to lookup for a simple row. So everything changes last week when I found out that I can run SQL queries…from VIM! Definitely not a silver bullet for my productivity but quite fun and interesting to see how extensible this old editor can be. Credits to the incredible Tim Pope who makes this ecosystem so exciting.

## A random line of code

Did you know that with React ref you can add a reference to your DOM elements and avoid looking them up in event handlers? Well…now you do! See this simple example from this quite comprehensive tutorial.

```
function App() {
  return (
    <ComponentWithDomApi
      label="Label"
      value="Value"
      isFocus
    />
  );
}

function ComponentWithDomApi({ label, value, isFocus }) {
  const ref = React.useRef(); // (1)

  React.useEffect(() => {
    if (isFocus) {
      ref.current.focus(); // (3)
    }
  }, [isFocus]);
 
  return (
    <label>
      {/* (2) */}
      {label}: <input type="text" value={value} ref={ref} />
    </label>
  );
}
```

## A random quote

> There is no single development, in either technology or management technique, which by itself promises even one order-of-magnitude improvement within a decade in productivity, in reliability, in simplicity.
> 
> Frederick P. Brooks, Jr.

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
