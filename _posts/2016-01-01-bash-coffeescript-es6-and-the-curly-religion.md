---
layout: post
title: Bash Coffeescript ES6 and the curly religion
---

> Looking back at the rise of ES6 transpilers, I can't help myself seeing the rise of an 'curly religion' vs 'other religion'.
> Time for a rant.

### The curly religion 

> C/C++ is the real deal. Be like C/C++.

The influence of this cute curlybrace syntax is obviously present in many other scripting languages.

### And lo, the curly religion was born.

<img src="https://lh3.googleusercontent.com/-v8eSHHGgrkM/TXGawKwNsFI/AAAAAAAAASY/i7L1XoPY6Sg/s1600/enlightening.gif"/>

### Traitors & apostates

Languages like Shellscript, VB, Python, Ruby, Coffeescript confuse the average curly follower.

> It's not curly, how can it be good.

A common trap for curly disciples, to identify themselves with their curly braces.
Anything indentbased, or human language-like seems too "_simplistic_".

### ES3 / ES4 / ES5 / ES6 / ES7

The brain of a curly follower is fixed on language versioning, since the tool itself became the holy grail.
Instead of focusing on the lowest common denominator, the highest common denominator becomes highprio.
The curly follower will start using ES8, and build ES8-to-ES5-tools to build ES5 applications.

    if ismoving ball
      move ball 3,8                            <- "BAD": no braces or linter needed
    
    if( ismoving( $ball ) ){
      move( $ball, array(3,8) );               <- "GOOD": so precise, so readable, so curly. 
    }

> thru the eyes of a curly disciple

### Curly vs Human language (HL) wars 

Let's take a step back, and compare:

 * C is a curly spec                             * Java(script) is a curly spec
 * C++ is a curly spec                           * ES6/7 is a curly spec
 * sh/bash/Lua are both tools and HL specs       * Coffeescript/Livescript/Purescript is a tool and a HL spec 
 * the kernel is a runtime                       * nodejs is a runtime
 * the gnu compiler converts to LCD (asm)        * Babel, Coffeescript etc converts to LCD (es3/es5 etc)

> LCD = Lowest common denominator

Clearly you can get impressive stuff done in both C or C++. See a pattern here?

DISCLAIMER: Clearly this overview is not 1-on-1 applicable 

### Stop using X! use X instead!

<img alt="" src="http://midlifexpress.com/wp-content/uploads/2013/03/rhetoric1.jpg" width="30%">

2015 was a year where forums flourished with what I call the unconscious _curly_ vs _human_ wars:

* developer X: Coffeescript is great!
* developer Y: Coffeescript sucks! _switch to_ ES6/7 while you can!

It would kindof be similar to:

* Developer X: C++ is great!
* Developer Y: (Linus torvalds) C++ sucks! _switch back to_ C while you can!

An obvious pattern here is that developer Y is using [FUD](https://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt) to manipulate developer X. 
Simple because of personal taste/history/fear of new things.

### The reality: the polyglot vs the disciple 

<img alt="" src="http://imgs.xkcd.com/comics/atheists.png"/>

A typical disciple is afraid of change, and hates because of selfprotection, perfectionism and lack of empathy.
The polyglot developer however, care's about solving problems in a lazy constructive way.

## Checklist: are you a disciple?

* Do you like ES6/7 because its the _next big thing_? 
* Do you use ES6/7 because 'everybody is using it' ?
* Do you hate ES5 because ES6/7 must be _superior_?
* Are you naturally fearful to learn/use HL tools (coffeescript/purescript/bash/haskell/ruby)?
* Are you fearful of functional programming?

Needless to say, the (fallicious) _coffeescript/typescript/ES6_ debate is clearly ran by curly disciples.

## A polyglot 

Enthousiast about anything which could get the job done.

## Conclusions 

* keep learning markup specs, formats and conventions (json/jsonschema/xml/wsdl)
* keep using tools to solve problems
* stop blaming, start emphasizing 
