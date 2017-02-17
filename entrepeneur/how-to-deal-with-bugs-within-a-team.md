How to deal with bugs within a team
===================================

<br>
<img align="right" src="/data/upload/images/comic/out/comic_userfoo.jpg"/>

### Quote ###

> *Chuck Norris writes code that optimizes itself*
>
> -- quote by unknown

### The issue ###

In [my previous article](/blog/how-to-not-become-a-reliability-engineer-for-every-project) I explained some aspects which can keep you focused on creative aspects of a project. However, this article will go more into details on how to design software which deal with errors for different environments/teams/servers.

### Some rules for your developers ###

  1. create a global logfunction (macro) and a plugin/module-related one (micro)
  1. each logcall can be of type: development, notice, warning, (soft) error
  1. buffer all logcalls in one array.
  1. upon error you write the full logbuffer into a new file (instead of appending)
  1. a soft error is an error, but it should not break execution
  1. notify hard errors (email/sms etc)
  1. *never* *never* print errors/uncaught exceptions to stdout
  1. write a close() function for your framework which is the only allowed function to call die() / exit() e.g.

The most important thing to remember is that you create different behaviours for different servers in a flexible way. This sounds like managing BS but this can simply be done by a one configuration file per server.

### Dev server ###

Important is that we see everything in the global+pluginlogs right away on the devserver:

<img src="/custom/pages/blog/entrepeneur/res/error_dev.png"/>

### Staging server ###

Lets not go into emailing here yet..

<img src="/custom/pages/blog/entrepeneur/res/error_staging.png"/>

### Live server ###

Here lets go into emailing + sms (make sure you throttle calls in a human way). Maximum one email + sms per hour on workdays and 1 per 3 hours during the weekend will be ok.

<img src="/custom/pages/blog/entrepeneur/res/error_live.png"/>

### Then, if everything is set.. ###  

Relax and enjoy! The key is to have this environment setup from the start.

`Disclaimer: the above guidelines are matching my taste, other configurations are also possible.` 
