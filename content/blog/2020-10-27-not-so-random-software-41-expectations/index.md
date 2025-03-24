---
title: "Not So Random Software #41 - Expectations"
date: 2020-10-27
categories: 
  - "newsletter"
tags: 
  - "elixir"
  - "machinelearning"
  - "opensource"
  - "statistics"
---

Hello everyone and welcome back to Not So Random Software!

This week I have been thinking about statistics and expectations. Mental models like statistical significance and p-values help us set expectations on what are the boundaries and conditions under which we are willing to accept something as true. Without them, what would be left with?

Enjoy the random walk!

## One article or paper

When does Predictive Technology become Unethical?

It is the generation of new data — the indirect discovery of unvolunteered truths about people — the makes machine learning predictions unethical? This HBR article investigates a few interesting cases.

## One video or podcast

Not So Standard Deviations 77 - Back to Statistics

You explain to students the concept of statistical significance, and the next question often is...and now what? how do we make a decision? Statistical significance is not as trivial as looking at an arbitrary threshold. It's a model that describes our inherent uncertainty about the world.

## One book

Statistics Done Wrong

Don't get yourself fooled by statisticians. When it comes to statistics, plenty of otherwise great scientists -- yes, even those published in peer-reviewed journals -- are doing statistics wrong. This book helps you avoid the most common traps.

## One tool

Open Source diagram tool - Diagrams.net

If you want to learn what does it take to build diagramming software in Javascript, this tool is free and open-source!

## One line of code

Curious about real world Elixir out there? here is a controller from this open source projects curated list.

```
  def index(conn, params) do
    current_user = Auth.current_user(conn)
    admin? = Auth.admin?(conn)
    page = ElixirStatus.Persistence.Posting.published(params, current_user, admin?)

    assigns = [
      postings: page.entries,
      page_number: page.page_number,
      total_pages: page.total_pages,
      created_posting: load_created_posting(conn),
      just_signed_in: params["just_signed_in"] == "true",
      referred_via_elixirweekly: params["ref"] == "elixirweekly",
      searching?: !is_nil(params["q"]),
      search_query: params["q"],
      current_posting_filter: params["filter"] |> nil_if_empty(),
      posting_filters: @posting_filters,
      search: params["q"] |> nil_if_empty(),
      changeset: changeset()
    ]

    conn
    |> ElixirStatus.Impressionist.record("frontpage")
    |> render("index.html", assigns)
  end
```

## One quote

> You are under no obligation to remain the same person you were a year ago, a month ago, or even a day ago. You are here to create yourself, continuously.
> 
> Richard Feynman

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
