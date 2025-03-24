---
title: "Not So Random Software #25 - Powerful questions"
date: 2020-05-05
categories: 
  - "newsletter"
tags: 
  - "actioncable"
  - "maps"
  - "questions"
  - "retrospective"
  - "stimulusjs"
---

Hello there and welcome back to Not So Random Software!

This week I am thinking about how to deliver powerful questions to others and yourself. Questions might feel intimidating or pointless, I get it; at the end of the day we are trying to get things done, and challenging every single decision can be detrimental to our productivity. On the other hand, many breakthroughs started by asking incredibly simple, but fundamental questions. Isaac Newton noticed an apple fall and simply asked himself: “If the apple falls, does the moon also fall?”. This question put Newton on the road to all his future accomplishments. So here is my reminder for keeping up with the exercise, even when you are experiencing temporary diminishing returns.

![Challenges-facing-transformation-too busy wheel - Rhizome](images/0O9lqF18zHpQQL4mmNXkyf7s3g7Vjtz8HzY3IrXKtc7JrGCg_VSvfn0IjniktMYhQCc789GyIImpP2XQF_T9t-L_KVYHaQPc-W405q6HZ5taWILjNETLKP9nPOhyX2sVED8YBep-Twf0Mau7lU4Vekc42zloOltd5Ko)

I hope you enjoy this selection of links!

## A random article or paper

Discovering first principles by using Socratic questioning

Socrates believed that the disciplined practice of thoughtful questioning enables the scholar/student to examine ideas and be able to determine the validity of those ideas. The link above puts such practice in the context of discovering first principles, i.e. irreducible truths you can use to explain reality. Here is what Socrates used to ask:

- Clarifying your thinking and explaining the origins of your ideas (Why do I think this? What exactly do I think?)
- Challenging assumptions (How do I know this is true? What if I thought the opposite?)
- Looking for evidence (How can I back this up? What are the sources?)
- Considering alternative perspectives (What might others think? How do I know I am correct?)
- Examining consequences and implications (What if I am wrong? What are the consequences if I am?)
- Questioning the original questions (Why did I think that? Was I correct? What conclusions can I draw from the reasoning process?)

## A random video or podcast

InfoQ presentation on Wardley Maps: Crossing the River by Feeling the Stones

Maps are a simple and effective tool to question reality. By positioning elements into a few dimensions you can challenge your model of reality and ask powerful questions about how the territory looks like and what practical decision you can do.

## A random book

What if: Serious scientific answers to absurd hypothetical questions

If you are following this newsletter you probably appreciate the value of randomness a bit. Jumping into something completely random every now and then is a very engaging way to build excitement. The same goes for questions! Asking random questions like the ones in this book might lead to unexpected (and certainly funny) insights.

## A random tool

Stimulus Reflex - Alternative to Phoenix live view to create realtime, reactive apps in Rails with no Javascript.

You have TODO web app and you want to mark an item as done without refreshing the page. Let's think this through; this involves hooking a javascript handler to the element, make an AJAX request, update the database, and finally update the DOM accordingly on success.

But why we landed into this solution? Using a map analogy, we might have had a mental map of the browser technology territory that lead us to design such a solution. But when was the last time you challenged your assumptions?

Stimulus Reflex does exactly that; by using the well-known Stimulus model together with web sockets, you can create reactive apps in Rails with almost zero custom Javascript.

## A random line of code

If you need to add an index to a big scary Postgres table, you don't need to be! By default, Postgres locks writes (but not reads) to a table while creating an index on it, which means your index creation might take hours. By using the CONCURRENTLY option for CREATE INDEX you can try your luck and build one hoping it's not going to be invalidated by a write.

```
class AddIndexToAsksActive < ActiveRecord::Migration
  disable_ddl_transaction!

  def change
    add_index :asks, :active, algorithm: :concurrently
  end
end
```

## A random quote

> I learned very early the difference between knowing the name of something and knowing something.
> 
> Richard P. Feynman

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
