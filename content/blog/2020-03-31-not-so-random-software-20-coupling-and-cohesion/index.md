---
title: "Not So Random Software #20 - Coupling and Cohesion"
date: 2020-03-31
categories: 
  - "newsletter"
tags: 
  - "cohesion"
  - "coupling"
  - "objectorientedprogramming"
  - "oop"
  - "softwaredesign"
  - "softwarequality"
  - "solid"
---

Hello there! This week I am thinking about coupling and cohesion; two seemingly simple but incredibly effective metrics to design systems both in the small and in the large. As usual, I am going to randomly pick some resources on this topic I have been reading over time, hope you enjoy!

## A random article or paper

The Conceptual Cohesion of Classes - An information retrieval approach to measuring class cohesion.

There is not such a standard to measure coupling and cohesion of classes. Most of the approaches in the literature (for OOP software) are largely based on the structural information of the source code, such as attribute references in methods. This paper proposes an intriguing set of measures for measuring cohesion based on the analysis of the semantic information embedded in the source code, such as comments and identifiers.

## A random video or podcast

All the little things

If we are talking about coupling and cohesion in practice I can't recommend enough Sandi Metz's talk at RailsConf 2014. It contains the famous quote _duplication is better than the wrong abstraction_ and helps you understand how to go from big problems to smaller components over a series of small straightforward refactoring steps.

## A random book

Practical Object Oriented Design in Ruby (POODR).

Following up from the previous video recommendation, the next obvious step is Sandi Metz's book on how to design OOP systems in Ruby; this book changed my perception of software. Among the many books and papers I read about software design — way more than a balanced person should — none was able to convey in simple terms the pragmatic application of OOP as concisely as this one; before reading this I literally felt lost in endless arguments about what good OOP looks like, now I am in peace!

## A random tool

Rubycritic

RubyCritic is a gem that wraps around static analysis gems such as Reek, Flay and Flog to provide a quality report of your Ruby code.

## A random line of code

Extracting pieces of computation that takes a standard input and giving them a name is an act of refactoring that helps both your cohesion and coupling. Ruby makes this easy with Proc!

```

proc = Proc.new { |a| puts a * 2 }
[1, 2, 3, 4, 5].each(&proc)
```

## A random quote

> Concurrent software development means starting development when only partial requirements are known and developing in short iterations that provide the feedback that causes the system to emerge. Concurrent development makes it possible to delay commitment until the last responsible moment, that is, the moment at which failing to make a decision eliminates an important alternative. If commitments are delayed beyond the last responsible moment, then decisions are made by default, which is generally not a good approach to making decisions.
> 
> Mary and Tom Poppendieck

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
