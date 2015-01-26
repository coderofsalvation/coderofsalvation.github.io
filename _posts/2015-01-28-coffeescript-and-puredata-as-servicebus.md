---
layout: post
title: Coffeescript and Puredata as Servicebus?
published: false
---

<div class="message">
  Howdy! In this post Im documenting my experiences with PureData and Coffeescript.
</div>

### The Case

For some reason, I've always been intrigued by visual programming environments.
It is a lot of fun to patch around and it feels less tiring to `program` things.
Think of modular synthesizer environments or a Servicebus on the web.
I had the crazy idea of mashing up some coffeescript inside PureData.

### PureData (PD)

[PD](http://en.wikipedia.org/wiki/Pure_Data) is an old beast in the field of visual programming languages.
It has a huge community, and tons of tutorials, youtube videos and patches available.

Luckily PD allows to send and receive network messages outside it's own box.
Great!
So this is what I came up with after discovering the ['port'-npmjs module](https://www.npmjs.com/package/port):

<img alt="" src="img/puredata-coffeescript.png"/>

### Results 

I didn't do any latency-tests, but I would be interested in using this setup to 
visualize webdata in realtime.
HTML5 is great and all that, but the PD-realm has its advantages too.
