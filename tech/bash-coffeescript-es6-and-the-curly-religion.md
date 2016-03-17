Bash vs Coffeescript vs ES6: the polytheists and the monotheist 
===============================================================

> Looking back at the rise of ES6 transpilers, I can't help myself seeing the rise of an 'curly religion' vs 'other religion'.
> Time for a rant.

### The curly religion 

I was there too. 
A developer grows up with the notion that C/C++ is the real deal.
The influence of this cute curlybrace syntax is obviously present in many other scripting languages (php/javascript and so on).
Wow, nodejs is like all that (C/C++/Javascript), wow!
And lo, the curly religion has been born.

### Human language is so not cool

Coffeescript was a huge blow in the faces of (unconscious) curly followers.
It is common trap for curly disciples, to start to dislike "_simplistic_" human language.

> _The brain of a curly follower is confused..what is this..ruby? or bash? or other programminglanguages I've been ignoring?
And where are the braces? My ego feels pain, I don't feel a clever developer anymore._

    if ismoving ball
      move ball 3,8                            <- coffeescript: not cool, confusing!
                                                  ..jsonschema even more confusing!
    
    if( ismoving( $ball ) ){
      move( $ball, array(3,8) );               <- js: definately cool, so precise!
    }                                             ..typescript even more confusing!

Heck, we might even define 'not cool' as 'programming for children'.
And lets not forget how cool/uncool it gets when doing _functional_ programming:

    update = compose when(ismoving), move      <- not cool
    update ball, [3,8]                                    

    if( ismoving( $ball ) ){
      move( $ball, array(3,8) );               <- functional programming 
    }                                             is cryptical and for losers!
                                                  lets just write real javascript

Do you agree? I hope not..

### Curly vs Human language (HL) wars 

Let's take a step back:

* Javascript is a curly spec
* ES6 is a curly spec
* Coffeescript is a tool and a HL spec 
* nodejs is a runtime
* Babel is a tool

Lets now compare this with the older days:

* C is a curly spec
* C++ is a curly spec
* Bash/Sh and Lua are both tools and HL specs 
* the kernel is a runtime
* the gnu compiler is a tool

See the pattern?

### Stop using javascript, use javascript!

2015 was a year where forums flourished with what I call the unconscious _curly_ vs _human_ wars:

* developer X: Coffeescript is great!
* developer Y: Coffeescript sucks! _switch to_ ES6 instead of coffeescript!

It would kindof be similar to:

* Developer X: C++ is great!
* Developer Y: (Linus torvalds) C++ sucks! _switch back to_ C!

The obvious pattern here is that developer Y is using [FUD](https://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt) to manipulate developer X. 
Developer Y is trying to stop people to use newer tool/spec XYZ, because of an personal taste/history.

### The reality: the polyglot vs the disciple 

A typical disciple is afraid of change, and hates out of selfprotection.
This is because the disciple _identifies_ him/herself with a curly- or human language.
The polyglot developer however, care's about solving problems in a lazy constructive way.
In short:

* the disciple would rather refuse to learn new things, out of fear of syntax-dislike and history
* the polyglot would rather learn new things, out of fear of unnecessary tasks/responsibilities.

## The polyglot 

. polyglot: (re)implement apache/memcache/database functionality in javascript (express)
. polyglot: learn make-syntax or bash or commandline linux tools.
. polyglot: write coffeescript to reduce syntaxnoise
. polyglot: write (or compile to) javascript because of curly disciples (with transpiler)
. polyglot: learn/use json specs (like jsonschema)
. polyglot: likes bash or coffeescript not because it's a _shorter_ syntax: its more _human_

## The disciple 

. a curly disciple: use typescript without knowing about jsonschema
. a curly disciple: refuse to learn/use HL tools (coffeescript or bash)
. a curly disciple: implement a build tool which performs certain _bash/sh_ commands in a particular order 
. a human disciple: implement that same tool but in coffeescript 

Popular things get hated on, like coffeescript.
Interestingly enough, the haters almost always are driven by curly disciple aspirations.

## Conclusions 

* keep learning markup specs, formats and conventions (json/jsonschema/xml/wsdl)
* keep using tools to solve problems
* refrain from HL- or curly language bias
* never blame a tool of spec, blame yourself for being ignorant.
