---
title: "Not So Random Software #35 - This is Water"
date: 2020-07-22
categories: 
  - "newsletter"
tags: 
  - "education"
  - "mindfulness"
  - "ruby"
  - "webdevelopment"
---

Hello everyone and welcome back to Not So Random Software!

This week has been one of reflection and thinking. It's often the case that I need multiple days to shut my conscious mind off and let the subconscious silently emerge. Often this process leads to thinking about your values, longer-term goals, and appreciation of what you have.

Enjoy the random walk!

## One article or paper

Heaven Beside You…Hell Within

I love this article as it's a great reminder that whenever you go, you are bringing yourself with you.

> We think we can escape from our job. From our problems. From our depression. From our low-grade dissatisfaction with our ordinary lives. But what do we find when we arrive to the exotic location? After we check in to the hotel or the Airbnb? We find, after the rush wears off, that we don’t feel any different. We brought ourselves with us…the true source of our unhappiness. 

## One video or podcast

This is water - commencement speech

David Foster Wallace's 2005 commencement speech to the graduating class at Kenyon College, is a timeless trove of wisdom. It's a reminder that we are self-centered by default and most of the time we do not realize what's happening around us. Our education is what empowers us to _choose what to think,_ and not _how to think._

## One book

Modern Front-end development for Rails

You probably have noticed already, but web development is getting more and more complex each year. If you need some guidance on how to approach the latest frontend challenges with Rails, this book does an excellent job.

## One tool

Bmg: A Ruby Relational Algebra

This tool is for the Rubyist out there who do a lot of in-memory data querying. A relational algebra (like SQL) can be very powerful to slice and dice your dataset. The fact you are not backed by a database shouldn't be a limiting factor to use this marvellous abstraction!

## One line of code

Ok it's meant to be one line of code...but I can't resist the temptation of posting the beauty of this minimalist state machine (Github here) written in Ruby. It's just 56 lines and it's as clear and simple as it can be! ❤️ Ruby

```
class MicroMachine
  InvalidEvent = Class.new(NoMethodError)
  InvalidState = Class.new(ArgumentError)

  attr_reader :transitions_for
  attr_reader :state

  def initialize(initial_state)
    @state = initial_state
    @transitions_for = Hash.new
    @callbacks = Hash.new { |hash, key| hash[key] = [] }
  end

  def on(key, &block)
    @callbacks[key] << block
  end

  def when(event, transitions)
    transitions_for[event] = transitions
  end

  def trigger(event, payload = nil)
    trigger?(event) and change(event, payload)
  end

  def trigger!(event, payload = nil)
    trigger(event, payload) or
      raise InvalidState.new("Event '#{event}' not valid from state '#{@state}'")
  end

  def trigger?(event)
    raise InvalidEvent unless transitions_for.has_key?(event)
    transitions_for[event].has_key?(state)
  end

  def events
    transitions_for.keys
  end

  def triggerable_events
    events.select { |event| trigger?(event) }
  end

  def states
    transitions_for.values.map(&:to_a).flatten.uniq
  end

private

  def change(event, payload = nil)
    @state = transitions_for[event][@state]
    callbacks = @callbacks[@state] + @callbacks[:any]
    callbacks.each { |callback| callback.call(event, payload) }
    true
  end
end
```

## One quote

> Nothing in life is as important as you think when you are thinking about it.
> 
> Daniel Kahneman

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
