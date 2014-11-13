---
layout: post
title: EBH, emergency break hooks to minimize risks for your webservice
---

<iframe src="//player.vimeo.com/video/106518767" width="100%" height="500" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe> 

<div class="message">
  Howdy! In this post I will explain some disastermanagement tricks for webservices.
</div>

### The Problem

Developing a webservice is easy, but it's tempting to overlook disastermanagement.
Maybe companies tell you otherwise, but *every* company experiences massive failures.
If you are one of the developers who thinks "unittests will keep us safe"...well..read on.

### We are humans, not Chuck Norris

> "The software failed because our tests did not expect this unexpected situation".

It doesn't matter how pro you are, at some point you/your team will have to deal with bugs.
This is a given fact, we make misstakes.
That's why this article promotes implementing emergency breaks, which allow developers to fix bugs
painlessly.
Best practice is to implement these from the start.

### Example

