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

### PureData (PD)

[PD](http://en.wikipedia.org/wiki/Pure_Data) is an old beast in the field of visual programming languages.
It has a huge community, and tons of tutorials, youtube videos and patches available.

### Downside of PD

In my opinion, the (Deutsch Limit](http://en.wikipedia.org/wiki/Deutsch_limit) becomes obvious very easily.
After a bit of fiddling, your screen will be filled with magical boxes and symbols.
A bit of code would certainly clean things up.

> Sure there are subpatches, but it becomes quite laborous tidying things all the time.

### Scripting language to the rescue

Luckily PD allows to send and receive network messages outside it's own box.
Great!
So this is what I came up with after discovering the ['port'-npmjs module](https://www.npmjs.com/package/port):

<img alt="" src="img/puredata-coffeescript.png"/>


