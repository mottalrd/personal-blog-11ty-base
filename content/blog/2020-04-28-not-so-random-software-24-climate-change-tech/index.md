---
title: "Not So Random Software #24 - Climate Change Tech"
date: 2020-04-28
categories: 
  - "newsletter"
tags: 
  - "carbonemissions"
  - "cleantech"
  - "climatechange"
  - "javascript"
  - "modulepattern"
---

Hello there and welcome back to Not So Random Software!

This week I stumbled upon the new documentary from Micheal Moore called Planet Humans and that pretty much took all my thinking. It's a good time to stop and reflect; we only have one planet.

I hope you enjoy this selection of links!

## A random article or paper

United Nations WESS Report 2018  
United Nations WESS Report 2011 - direct comment on the limits of mainly relying on technology to solve climate change

I found out that the United Nations publishes a World Economic and Social Survey publication (WESS) every few years highlighting the main problems humanity is facing; climate change being one of those. The report published in 2011 perfectly describes the current situation; we are relying too much on a technological panacea and too little on limiting our infinite desire for growth on a limited planet.

> In order to take pressure off the technological innovation imperative, individual limits of 70 gigajoules (GJ) primary energy use per capita and 3 tons of carbon dioxide (CO2) emissions per capita by 2050 may need to be considered.

You produce 3 tons of CO2 with one return flight London-New York, plus a normal diet with some meat in it over the course of one year. That's it.

## A random video or podcast

Micheal Moore - Planet of Humans

Micheal Moore's new documentary is open for all on Youtube. It challenges the common belief that renewable energy technology is the right solution to climate change. Even if half of what he says is true, we are in big trouble; we are exploiting the planet's natural resources way too fast for technology to save us. We are now burning trees to produce energy, FGS. And if you are tempted to reconsider nuclear power again (with this documentary) be aware it's the same fallacy again; we need to limit our infinite desires for growth in a finite planet.

## A random book

The Story of Stuff

Ok, I get it; we should rely less on technology and limit our own growth. Let's get practical, shall we? The Story of Stuff presents a direct link between your personal overconsumption and the effect on the environment, the economy, and our health. The author shares concrete steps for taking action at the individual and political level that will bring about sustainability, community health, and economic justice.

## A random tool

An Open Source Carbon Estimator

This is a software newsletter right? So obviously if the problem is awareness and overconsumption we can totally build a thing, right? I strolled around the web and found incredibly hard to have a 5 minutes answer to what my consumption is. You need to estimate your bills, translate daily usage into yearly ones, etc. That's not going to work for the late majority.

This open-source solution does reduce the questionnaire to a few questions and put it into context depending on where you live, in this case, Singapore. I will create a fork for London in due time! Also, the fact that co2 emissions estimates are open in spreadsheet format is very good for transparency; some of those are really hard to estimate.

## A random line of code

Ok let's turn back to pure tech for a second. I was fascinated recently by how the React hooks work; it seemed like the kind of magic feeling Rails delivers. I couldn't resist digging in and see how it actually works. This excellent article describes it in detail; here is the tiny React hook example presented. It's all about functional state!

```
const MyReact = (function() {
  let _val // hold our state in module scope
  return {
    render(Component) {
      const Comp = Component()
      Comp.render()
      return Comp
    },
    useState(initialValue) {
      _val = _val || initialValue // assign anew every run
      function setState(newVal) {
        _val = newVal
      }
      return [_val, setState]
    }
  }
})()
```

and here is how you use it

```
function Counter() {
  const [count, setCount] = MyReact.useState(0)
  return {
    click: () => setCount(count + 1),
    render: () => console.log('render:', { count })
  }
}
let App
App = MyReact.render(Counter) // render: { count: 0 }
App.click()
App = MyReact.render(Counter) // render: { count: 1 }
```

## A random quote

Two this week...because we need a bigger dose of wisdom after all of that.

> You act like mortals in all that you fear, and like immortals in all that you desire.
> 
> Seneca

> There is only one liberty, to come to terms with death. After which, everything is possible.
> 
> Albert Camus

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
