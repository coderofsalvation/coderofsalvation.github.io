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

### Routing in code 

Depending on your project, static routing of messages in code can become evil.
Loose coupled routing is a lot more flexible, but it'll still requires:

* a proper editorGUI
* a proper dataformat

In my past I've build things like this, or looked at applications like this (servicebus).
As will all things, it's always worth looking for free existing tools.

> Benefits: stability, community, focus on your core problem

I was wondering if could use PureData as a flexible, visual router of messages, and 
coffeescript for processing.

### PureData (PD)

[PD](http://en.wikipedia.org/wiki/Pure_Data) is an old beast in the field of visual programming languages.
It has a huge community, and tons of tutorials, youtube videos and patches available.

Luckily PD allows to send and receive network messages outside it's own box.
Great!
So this is what I came up with after discovering the ['port'-npmjs module](https://www.npmjs.com/package/port):

<img alt="" src="img/puredata-coffeescript.png"/>


