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

> The downside however is: it needs code, therefore a developer specialist, database, server infrastructure etc. Automation still doesn't look simple.

Jeff Lindsay, a friend at Gliderlabs (who coined the term *'webhooks'*) did a great job promoting the idea of 'the evented web'.
Back then, it gave me these revelations: 

* 'polling-data-syndrome' is a thing 
* *"Developers like to develop (too much)"*
* This pushes a 'web as a newspaperstand'-illusion to people

## IFTTT 

IFTTT was already around back then, and demonstrated this philosphy as well:

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

> Mo code, mo problems. Mo yahoo-pipe-ish solutions, mo [deutchs limit](https://en.wikipedia.org/wiki/Deutsch_limit) 

Offering automations with a *'conditional/chainable character unlike IFTTT'* creates new challenges.
It's no longer an adapter-platform (IFTTT), but a programming-silo which introduces all kinds of new risks.

> IFTTT seems to be the only one which promotes the eventful web, and a "Don't build silo's"-attitude. This might explain why IFTTT is attractive by nondevelopers and developers.

## The secret of IFTTT?

I have no idea, but here's my gut-feeling :)

> In order to pull something off like IFTTT, I think 3 things are important:

* understand the human needs
* understand the technical challenges 
* create a universal solution for developers and nondevelopers 

Imho IFTTT got it right from the beginning, by selling simplicity instead of complexity.
It makes something incredibly complex very simple.

# Why I think IFTTT is ahead of the game

> Where others offer more complex solutions, IFTTT somewhat follows [the rule of least power](https://en.wikipedia.org/wiki/Rule_of_least_power).

IFTTT seems to be layered in a smart, interconnected way:

| layer |what                | used by | for | how |
|-------|----------------|----|-----|-----|
| 1 | userinterface          | nondevelopers | nondevelopers | sharing applets |
| 2 | applet service         | developers | nondevelopers | ([see here](https://platform.ifttt.com/docs/api_reference)) |
| 3 | backoffice integration | developers | products |  embed / list / show / enable / disable applets  ([see here](https://platform.ifttt.com/docs/embedding_applets#list-applets)) |

> NOTE: I've only noticed layer 3 by accidentally googling it. Ideally, the distinction between layer 2-3 could be more obvious in the IFTTT Platform docs,

I was also impressed by this REST endpoint validator:

<img src="/public/img/ifttt-onboarding.png"/>

> This turns a very hairy human process (usually emailing back'n'forth with support) into a bunch of green lights. 

In case you're curious about IFTTT Platform's onboarding process for applet services: I've made this [node-ifttt-express repository](https://github.com/coderofsalvation/node-ifttt-express) to setup your own IFTTT Platform applet.

# Conclusion 

The trigger-action-paradigm offers a more flexible & eventful future for SaaS.
IFTTT demonstrates that limiting webintegrations to an adapter-platform (unlike zapier) don't really get in the way of developers.
I hope it will become a standard, and will wake up other companies as well.

