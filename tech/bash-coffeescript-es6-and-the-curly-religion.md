Bash Coffeescript ES6 and the curly religion
============================================

> Looking back at the rise of ES6 transpilers, I can't help myself seeing the rise of an 'curly religion' vs 'other religion'.
> Time for a rant.

### The curly religion 

I was there too. 
A developer grows up with the notion that C/C++ is the real deal.
The influence of this cute curlybrace syntax is obviously present in many other scripting languages (php/java(script) and so on).
Nodejs seems to bridge the whole stack from C/C++ to javascript.
And lo, the curly religion has been born.

<img src="https://lh3.googleusercontent.com/-v8eSHHGgrkM/TXGawKwNsFI/AAAAAAAAASY/i7L1XoPY6Sg/s1600/enlightening.gif"/>

### Therefore, thou shalt only like curly braces 

Coffeescript was a huge blow in the faces of (unconscious) curly followers.
It is a common trap for curly disciples, to start to dislike "_simplistic_" human language.

> _The brain of a curly follower is confused..what is this..ruby? or bash? or other programminglanguages I've been ignoring?
And where are the braces? My ego feels pain, I don't feel a clever developer anymore._

    if ismoving ball
      move ball 3,8                            <- coffeescript: not cool, confusing!
                                                  ..jsonschema even more confusing!
    
    if( ismoving( $ball ) ){
      move( $ball, array(3,8) );               <- js: definately cool, so precise!
    }                                             ..typescript even more precise!

Heck, we might even define 'not cool' as 'programming in basic'.
And lets not forget how cool/uncool it gets when doing _functional_ programming:

    update = compose when(ismoving), move      <- not cool
    update ball, [3,8]                                    
    
    if( ismoving( $ball ) ){                   <- #$%@ functional programming!
      move( $ball, array(3,8) );
    }                                          

### Curly vs Human language (HL) wars 

Let's take a step back:

* Java(script) is a curly spec
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

Clearly this is not 1-on-1 applicable, but C/C++ Bash/sh/Lua have never disappeared, despite the love/hate.
See a pattern?

### Stop using X! use X instead!

<img alt="" src="http://midlifexpress.com/wp-content/uploads/2013/03/rhetoric1.jpg"/ width="30%">

2015 was a year where forums flourished with what I call the unconscious _curly_ vs _human_ wars:

* developer X: Coffeescript is great!
* developer Y: Coffeescript sucks! _switch to_ ES6 while you can!

It would kindof be similar to:

* Developer X: C++ is great!
* Developer Y: (Linus torvalds) C++ sucks! _switch back to_ C while you can!

The obvious pattern here is that developer Y is using [FUD](https://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt) to manipulate developer X. 
Developer Y is trying to stop people to use newer tool/spec XYZ, because of an personal taste/history.

### The reality: the polyglot vs the disciple 

<img alt="" src="http://imgs.xkcd.com/comics/atheists.png"/>

A typical disciple is afraid of change, and hates out of selfprotection.
This is because the disciple _identifies_ him/herself strictly with a curly- or human language.
The polyglot developer however, care's about solving problems in a lazy constructive way.
In short:

* the disciple would rather refuse to learn new things, out of fear of syntax-dislike and history
* the polyglot would rather learn new things, out of fear of unnecessary tasks/responsibilities.

## The disciple syndrome

* a curly disciple: likes ES6 because its the _next big thing_ 
* a curly disciple: hates ES5 because ES6 is _superior_
* a curly disciple: uses typescript without knowing about jsonschema spec
* a curly disciple: refuse to learn/use HL tools (coffeescript or bash)
* a curly disciple: will aggressively express dislike of shellscript/[powscript](https://github.com/coderofsalvation/powscript)/coffeescript/ruby/python etc
* a curly disciple: fearful of functional programming

Needless to say, the (fallicious) _coffeescript/typescript/ES6_ debate is clearly ran by curly disciples.
Polyglots just don't care.

## Conclusions 

* keep learning markup specs, formats and conventions (json/jsonschema/xml/wsdl)
* keep using tools to solve problems
* stop blaming 
