Dividing a webproject into seperate subsystems
==============================================

<br>
<img src="/data/upload/images/comic/out/comic_divide.jpg" align="right" width="30%"/>

### Quote ###

> *Always code as if the guy who ends up maintaining your code,<br>
> will be a violent psychopath who knows where you live.*
>
> — Rick Osborne

### Why ###

Sometimes a big webproject can become too advanced to share the workload.<br>
Documenting everything would be a good step, or not?

### Why divide instead of go deeper ###

Documenting would mean 'going deeper', and this is not always the best solution.
Usually when one is in a situation like stated above, it means RAD got out of hand, and 
the software is doing too much.<br>
At work, we had a similar problem, the software was just doing too much.
The introduction of new features became too risky, and even putting other programmers on 
it (who had the benefit of time) would not decrease any risks.
Therefore, documenting does not always add value.

### How to divide ###

Dividing a webproject can be done in many ways, and it all depends on the situation.
At work, we decided to split up the current webproject into several subsystems:

  * Every subsystem is portable, and can sit on any server.
  * Servers can communicate with one another without http (slow)
  * central database which prevents raceconditions by demanding transactional queries
  * Every subsystems does something unique:
    * API's
    * Outward communication (email/sms)
    * Userprofiles
    * Database/Files/CloudFiles
    * backend A
    * backend B
    * and so on.

If you look at the last aspect, there is a big win in it.
Many programmers can now by plugged into several areas without having to understand everything in detail.
Also, there is no risk of having one programmer being responsible for everything, so this makes a shared workload truely possible.
The inter-subsystem communication ensures that subsystems can be implemented in different programming languages.
Also, many legacy-decisions or codesmell in the current webproject can be solved/designed/improved in the new subsystems.

### First Stage ###

First stage is to analyze, and sketch out the current inner workings of your webproject.

  * Reserve one total day for a brainstorm
  * Get a sketchbook
  * Sit with the team and draw the most important parts.
  * Then stop, and create on an empty page the ultimate `serverpark`
  * every drawn box will be a subsystem, and think about where which information should be
  * give your subsystems fun silly names to keep things positive
  * with every decision ask yourself: *What would google do?*
  * think about symbolic links for mounted/shared network directories
  * think about how every subsystem would get databasedata..directly? or thru another subsystem
  * think about what subsystem/user-specific data should be stored where
  * After the brainstorm, put it into a digital diagram (using graphviz etc) 
  * print it out *BIG* and put it on the wall, and attach a pencil to it.
  
Now you have a startingpoint to talk about.
No more hours of talking before getting to the point, just a finger on the diagram should be enough.
Here is an example of a start of your `serverpark`:

<br>
<img src="/custom/pages/blog/entrepeneur/res/graphviz.png">
<div style="clear:both"></div>

### Next Stages ###

Designing is fun, but how to transform from current situation to the future?
Simply by starting development of the subsystems, and postponing feature(requests) which 
should be implemented in those subsystems.
Why?

  * Because it introduces major stability risks, and it has to stop.

I have stressed in other articles, that good developerteams can say no sometimes, and stockholders will be happy about it.
In the end everybody wants a stable product & the businessmodel, so pesky features are not worth it in this situation.
So, slowly the subsystems will start working, and feature-by-feature one can migrate functionality to subsystems.
Because of inter-subsystemcommunication, one can replace implementationcode in the original webproject by sending triggers
to the appropriate subsystem.
