---
layout: post
title: Why IFTTT is ahead of the game
---

<img src="/public/img/ifttt.jpg"/>

<div class="message">
  Hi! In this post I'll try to explain why I think IFTTT is ahead of the game.
</div>

## First a bit of history 

When I started out, unix pipes were (and still are) superpowerful to automate things:

    $ echo "mail -s "$USER: please do a server-update" john@mycompany.com" | at 1145 jan 31

> It looks quite humanreadable..kindof :)

## Then Yahoo pipes happened 

Interactive websites were mostly limited to data-entry & form-processing.
Yahoo made great efforts to create an eventful web:

<img src="/public/img/yahoopipes.jpg"/>

> Impressively as it was, somehow this doesn't look simple :)

## SOAP & REST became a thing

<img src="/public/img/rest.png"/>

> The downside however is: its needs a developer specialist, a database infrastructure etc. Automation still doesn't look simple.

Jeff Lindsay, a friend at Gliderlabs (who coined the term *'webhooks'*) did a great job promoting the idea of 'the eventful web'.
It gave me this revelation: *"Developers like to develop (too much)"*

## IFTTT 

IFTTT was already around back then, so I looked at this:

<img src="/public/img/ifttt-if-this-then-that.jpg"/>

And I looked at the unix oneliner again:

    $ echo "mail -s "$USER: please do a server-update" john@mycompany.com" | at 1145 jan 31

> Do you notice the simplicity in both approaches?

* it's very highlevel: it abstracts code and complexity away 
* emphasis on on human language & perception
* we don't need specialists anymore :)

## Now let's look at the competition

Over the years, lots of competitors have arised (Microsoft Flow, Zapier), ESB's (mulesoft,JBoss), and 
opensource solutions like node-red, datafire etc.
I've even designed and implemented some solutions for customers myself :)

> The blind spot of the competitors?

*"Abstracting away logic, by introducing new logic is not a solution"*

<img src="https://www.explainxkcd.com/wiki/images/d/d6/manuals.png" />

Being *'more conditional/chainable than IFTTT'* isn't really a win imho.
It introduces a new 'specialist'-trap, therefore it'll invite human error.
What if the carefully crafted automation-chain breaks?

> Who to blame? :) 

## The secret of IFTTT?

No idea, but here goes :)

> In order to pull something off like IFTTT, I think 3 things are important:

* understand the human challenges
* understand the technical challenges 
* filter out noise, and reduce it to its essence

Imho IFTTT got it right from the beginning, by selling simplicity instead of complexity.
IFTTT is a lion with the friendly face of a cow: it makes something incredibly complex, very simple.

# Why I think IFTTT is lightyears ahead

I'm very thankful to have had experience with highrisk, highvolume webintegrations. I've done some important B2B integration-projects using booking.com, airbnb, expedia etc.
I kindof know what to expect/offer when using/designing API's:

* a sandbox and production API
* documentation
* back-and-forth emailing with the supportdesk
* certification scenario by phone etc.

Eventhough these companies did an incredible job at helping us, it's not anywhere near THIS:

<img src="/public/img/ifttt-onboarding.png"/>

> IFTTT platform turned a very hairy human process into a bunch of green lights. 

The fact that the IFTTT Platform wasn't just designed as a REST api tells me that they're innovative.
I've designed some fairly good API onboarding-processes for sales, but IFTTT Platform completely blows that away.
Also, the trigger-action-paradigm offers a bright future for SaaS-design.
I hope it will become a standard at some point.
