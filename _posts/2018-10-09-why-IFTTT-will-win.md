---
layout: post
title: Why IFTTT will win 
---

<img src="/public/img/ifttt.jpg"/>

<div class="message">
  Hi! In this post I'm explaining why I think IFTTT is three steps ahead with the rest of the world.
</div>

## First a bit of history 

When I started out, unix pipes were (and still are) a superpowerful to automate things:

    $ echo "mail -s "$USER: please check free diskspace" john@mycompany.com" | at 1145 jan 31

> It looks quite humanreadable to some extent


## Then Yahoo pipes happened 

Interactive Websites were mostly limited data-entry & form-processing.
Yahoo made great efforts to create an eventful web:

<img src="/public/img/yahoopipes.jpg"/>

> Impressively as it was, somehow this doesn't look simple.

## Then REST became a thing

<img src="/public/img/rest.png"/>

> The downside however is: now we need a developer specialist, a database infrastructure etc. Automation still doesn't look simple.

## At the same IFTTT was launched

Now look at this:

<img src="/public/ifttt-if-this-then-that.jpg"/>

And let's look at the unix oneliner again:

    $ echo "mail -s "$USER: please check free diskspace" john@mycompany.com" | at 1145 jan 31

> Do you notice the simplicity in both approaches?

* it abstracts code and complexity away 
* this makes integration code-agnostic
* this allows emphasis on human language & perception
* we don't need specialists anymore

## Now let's look at the competition

Over the years, lots of competitors have arised (Microsoft Flow, Zapier) as well as ESB's (mulesoft etc), as well as 
opensource solutions like node-red, datafire etc.
Heck, I've even designed and implemented some solutions for customers myself :)

> My / Their misstake?

*"Abstracting away logic, by introducing new logic is not a solution"

Also, the competitors usually promote USP's like 'more conditional/chainable than IFTTT'.
However, this is a misstake imho.
Introducing userdefined logic, introduces a new 'specialist'-trap, therefore more human error.
What if the carefully crafted automation-chain breaks?

> Who to blame? :) 

<img src="https://www.explainxkcd.com/wiki/images/d/d6/manuals.png" />

> In order to pull something off like IFTTT, one really needs to understand the problem on a human- and technical-level.

Imho IFTTT got it right from the beginning, by selling simplicity instead of complexity.
IFTTT is a lion with face of a cow: it makes something incredibly complex very simple.

# Why I think IFTTT is lightyears ahead

I'm very thankful to have had experiences with highrisk, highvolume webintegrations (I've done some important B2B integration-projects with booking.com, airbnb, expedia etc).
I kindof know what to expect or to offer:

* a sandbox and production API
* documentation
* back-and-forth emailing with the supportdesk
* certification scenario by phone etc.

Eventhough these companies did an incredible job at helping us, it's not anywhere near this:

<img src="/public/ifttt-onboarding.png"/>

> IFTTT platform turned a very hairy human process into a bunch of green lights. 

The fact that the IFTTT Platform wasn't just designed as a REST api tells me that they know something.
I've designed some fairly good API onboarding-processes for sales, but IFTTT Platform completely blows that away.





