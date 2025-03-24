---
title: "Not So Random Software #19 - Autonomous Teams"
date: 2020-03-26
categories: 
  - "newsletter"
tags: 
  - "microservices"
  - "softwarequality"
  - "teams"
---

Hello there! This week I am going to explore the relationship between roles and responsibilities both in Software end Teams. Hope you enjoy the ride!

## A random article or paper

Conway's law original paper

In 1967 Melvin E. Conway submitted a paper called "How Do Committees Invent?" to the Harvard Business Review. HBR rejected it on the grounds that the author did not prove their thesis. I then submitted it to Datamation, the major IT magazine at that time, which published it April 1968. The paper was then cited in the classic book "The Mythical Man-Month" by Fred Brooks, calling it "Conway's Law." The name stuck and it is famous since then.

> Because the design that occurs first is almost never the best possible, the prevailing system concept may need to change. Therefore, flexibility of organization is important to effective design.

## A random video or podcast

What We Got Wrong: Lessons from the Birth of Microservices

Ben Sigelman worked at Google from 2003 to 2012 and talks about the _microservices_ journey there, the lessons learned along the way and how to apply those lessons today.

## A random book

Good Strategy Bad Strategy.

With the ever-increasing advice of giving teams mastery, autonomy and purpose (Daniel Pink, https://www.goodreads.com/book/show/6452796-drive) the role of the IT leaders might become more and more puzzling over time. CIO Mark Schwartz is helping me reflect on how to make such a role an integral part of the value creation engine so that IT doesn't merely become a service function but a strategic enabler.

CIO Executive Council studied how business stakeholders perceive IT, this is what they found and how Schwartz comments on it.

> Fifty-eight percent said that IT was perceived as a service provider or just a cost center; 28% as a separate but partnering group; 11% as a peer; and just a startling 3% as a business game changer. I haven’t seen a study on this, but what percentage of respondents would say that technology itself — as opposed to the IT department — is a business game changer? High, I’d think. What then does it tell us that only 3% think that the IT department is a business game changer?

## A random tool

Zeebe: A Workflow Engine for Microservices Orchestration

I dream about empowering non-technical stakeholders to build their own workflows. Services like Zapier are a stepping stone in this direction. I have been hearing good things about Camunda from the Thoughtworks tech radar and my understanding is that Zeebe should be the cloud-based evolution of that, as described here.

> Zeebe allows users to define orchestration flows visually using BPMN, the popular standard for Business Process Modeling. Zeebe ensures that once started, flows are always carried out fully, retrying steps in case of failures. Along the way, Zeebe maintains a complete audit log so that the progress of flows can be monitored and tracked. Zeebe is a big data system and scales seamlessly with growing transaction volumes.

## A random line of code

Did you know that you can build SVG images using Javascript code using SnapSVG? Well, now you do!

If you are like me and confused about SVG versus an HTML5 canvases, then I'll save you the Google search. HTML canvas is raster-based, while SVG is vector-based, which in short means it is more efficient. If attributes of an SVG object are changed, the browser can automatically re-render the scene. If you do the same using canvas, the entire scene would need to be redrawn.

```
// https://codepen.io/mottalrd/pen/ZEGmJLL
// First lets create our drawing surface out of existing SVG element
// If you want to create new surface just provide dimensions
// like s = Snap(800, 600);
var s = Snap("#svg");
// Lets create big circle in the middle:
var bigCircle = s.circle(150, 150, 100);
// By default its black, lets change its attributes
bigCircle.attr({
    fill: "#bada55",
    stroke: "#000",
    strokeWidth: 5
});
// Now lets create another small circle:
var smallCircle = s.circle(100, 150, 70);
```

## A random quote

> Teams that lack trust are incapable of engaging in unfiltered and passionate debate of ideas. Instead, they resort to veiled discussions and guarded comments.
> 
> Lencioni, Patrick M.. The Five Dysfunctions of a Team

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
