---
layout: post
title: Why IFTTT is ahead of the game
---

<img src="/public/img/ifttt.jpg"/>

<div class="message">
  Hi! In this post I'll try to explain why I think IFTTT is ahead of the game. Disclaimer: I'm not related with (or paid by) IFTTT in any way.
</div>

## First a bit of history 

When I started out, unix pipes were (and still are) superpowerful to automate things:

    $ echo "mail -s "$USER: please do a server-update" john@mycompany.com" | at 1145 jan 31

> It looks quite humanreadable..kindof :)

## Then Yahoo pipes happened 

Interactive websites were mostly limited to data-entry & form-processing.
Yahoo made great efforts to create an eventful web:

<img src="/public/img/yahoopipes.jpg"/>

> For that time it was very impressive, but somehow this doesn't look simple :)

## SOAP & REST became a thing

<img src="/public/img/rest.png"/>

> The downside however is: it needs a developer specialist, database, server infrastructure etc. Automation still doesn't look simple.

Jeff Lindsay, a friend at Gliderlabs (who coined the term *'webhooks'*) did a great job promoting the idea of 'the eventful web'.
It gave me this revelation: *"Developers like to develop (too much)"*
No more polling, I was cured!

## IFTTT 

IFTTT was already around back then, which looks like this:

<img src="/public/img/ifttt-if-this-then-that.jpg"/>

Now lets look at the unix oneliner again:

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

*"Abstracting away logic by introducing highlevel scripting to the user, is a solution which creates a new problem"*

<img src="https://www.explainxkcd.com/wiki/images/d/d6/manuals.png" />

Offering automations which are *'conditional/chainable unlike IFTTT'* isn't really a win, it's a problem imho.
It claims to take away the need for developers, but at the same time its complexity requires different developers.
What if a carefully crafted automation-chain breaks?
> Who to call? :) 

It seems that IFTTT is the only one which hits the sweepspot, by minimizing risks for themselves and their users.

> Mo code, mo problems. Mo yahoo-pipe-ish solutions, mo [deutchs limit](https://en.wikipedia.org/wiki/Deutsch_limit) 

## The secret of IFTTT?

I have no idea, but here's my gut-feeling :)

> In order to pull something off like IFTTT, I think 3 things are important:

* understand the human needs
* understand the technical challenges 
* target both developers and nondevelopers 
* create a universal solution 

Imho IFTTT got it right from the beginning, by selling simplicity instead of complexity.
It makes something incredibly complex very simple.

# Why I think IFTTT is ahead of the game

I'm very thankful to have had experiences with highrisk, highvolume webintegrations. I've done some rewarding B2B integration-projects using booking.com, airbnb, expedia etc.
I know the challenges of designing & implementing an API or connector, and what developers expect:

* a sandbox and production API
* documentation
* back-and-forth emailing with the supportdesk
* certification scenario by phone etc.

Eventhough these companies did an incredible job at helping us, it's not anywhere near something like this:

<img src="/public/img/ifttt-onboarding.png"/>

> IFTTT platform turns a very hairy human process into a bunch of green lights. 

The fact that the IFTTT Platform wasn't just designed as a classical REST api + documentation, tells me they're ahead of the game.
I've designed some fairly nice API onboarding-processes for sales, but IFTTT Platform completely blows that away.
Also, the trigger-action-paradigm offers a better future for SaaS-design & collaboration imho.
I hope it will become a standard, and will wake up other companies as well.

> In case you're curious about IFTTT Platform's onboarding process, I made this [node-ifttt-express repository](https://github.com/coderofsalvation/node-ifttt-express) to setup your own IFTTT Platform applet.
