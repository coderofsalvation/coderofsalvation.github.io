---
layout: post
title: EBH, emergency break hooks to minimize risks for your webservice
---

<div class="message">
  Howdy! In this post I will explain some disaster-management tricks for webservices.
</div>

### The Problem

Developing a webservice is easy, but it's tempting to overlook disaster-management.
Maybe companies tell you otherwise, but *every* company experiences massive failures.
If you are one of the developers who thinks "unittests will keep us safe"...well..read on.

### We are humans, not Chuck Norris

> "The software failed because our tests did not expect this unexpected situation".

It doesn't matter how pro you are, at some point you/your team will have to deal with bugs.
This is a given fact, we make mistakes.
That's why this article promotes implementing emergency breaks, which allow developers to fix bugs
painlessly.
Best practice is to implement these from the start.

### Modularity, from a designers dream to a developers nightmare

Creating scalable applications is great, but it can become out of control when there's no
 central control (an EBH).

### Example EBH

Here's a basic set of emergency break hooks API:

<img src="/public/img/EHB.png"/>

### Explanation

The flowchart above illustrates a 'macro-api'.
Basically it is your webservice exposed as an REST UNIX Daemon.
On the left you'll see api-entrypoints (the emergency breaks) which can be called thru Hubot or any other backend.

> NOTE: when I use the word `component` it can mean `frontend`, `backend`, `api`, `esb`, `queue`, `servers` etc.

* start - start all components using REST-calls
* stop - stops all components using REST-calls
* maintenance - in case of heavy problems: let API + website output a maintenance message
* cleanup - do REST calls to components (to clean up database, cache e.g.)
* test - emits REST-calls to all components, so they can run a few  unittest to ensure basic integrity
* backup - emits REST-calls to all components, so they can write backup files e.g.
* status - allow all components to obtain the overall status (can prevent triggering test emails e.g.)

### Conclusion

EHB traditionally exist as UNIX cli-commands, but can also be thought of as an REST macro-controller.
