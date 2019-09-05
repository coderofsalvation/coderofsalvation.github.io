MoSCoW and RAD = Peace of mind
==============================

<br>
<img align="right" src="/data/upload/images/comic/out/comic_moscow.jpg"/>

### Quote ###

> *If you don't plan to achieve rapid development, you can't expect to achieve it.*
>
> -- quote by [Steve Mcconnel](http://www.stevemcconnell.com/rdenum.htm)

### What is RAD ###

Rapid application development (R.A.D) is a software development methodology that uses minimal planning in favor of rapid prototyping. 

### The reality ###

Everybody agrees with **Rapid Development** and **planning stuff**.
But it can be tempting for developers & managers to think like : *"Hey if we forget about planning stuff, we 
can do more **rapid development**!"*.
When dealing with serious projects, this is a myth imho.

### Side Product: Confusion on time ###

*Planningless* RAD might be ok for a while, but at some point, as the project becomes more and more succesfull, soon:

  * more and more features need to be implemented.
  * the developers will realize its too risky to deploy/upgrade productioncode every day.
  * the developers realize, that they dont feel confident about the software.
  * more and more the focus will have to go to testing and riskmanagement
  * the staff experiences an unhealthy bugs/feature-ratio
  * the idea of *lets plan!* gets easily rejected "*because we always worked like this from the start*"

Anyways, without planning, nobody knows anymore what can be done succesfully in any given timeframe.

### Side Product: Hypnosis ###

It became too big, the RAD-methology starts too work against the team.
If the team is ignorant about this, usually the negative effects are
'solved' using a traditional counterproductive method:  hypnotising/manipulating eachothers.

  * Manager to Developer-hypnosis on the last day before update: `can you pleeease also do feature x before tomorrow?`
  * Manager to Developer-hypnosis: `Why is feature y in the next update, and x is not?`
  * Developer to Manager-hypnosis: `Look its RAD ok..we agreed on not planning stuff to get feature z in this upgrade`
  * Manager to Developer-hypnosis: `Its always a mystery what will be in the next release`
  * Developer to Manager-hypnosis: `I can add the small logo..but it will take me 5 days to test all platforms`

### Longterm RAD Project results ###

  * Having the illusion that RAD will give turbo to your project
  * Starting off with highquality planning-ethos, and ending up with none
  * Stockholder x is not happy because his proposed feature isnt in the update 
  * Code-smell: hairy code will control the developers instead of vice versa
  * Worstcase: people will start pointing fingers to one another

### Why ###

RAD doesnt really force people to say- or expect a 'no' during upgrades.
Development needs a 'no' sometimes, and usually good programmers can say 'no'.
Approved Feature/BugFix-requests usually get associated with 'promises' (a *yes*), this is a big danger.
The IT catchphrase *The sky is the limit*, should be rephrased in this case to *The 'yes' is the limit*.

### Solution: Keep it RAD and real ###

So how to go from RAD to Planned RAD?
I've tried many software development metholodies, but throughout the years I've found this particular combination very powerfull:

  * RAD
  * MoSCoW

### What is MoSCoW ###

The MoSCoW-method is a priority-system in future software development iterations (updates).
If you would ask me, I would call it "keeping things real" between the staff/devteam/stakeholders.
MoSCoW kills false expectations, because every approved feature- or bugfix-request is categorized democratically like this:

  * M - must haves   (must be in the next upgrade)
  * S - should haves (very wanted functionality, but upgrade is usable without them)
  * C - could haves  (if there's enough time)
  * W - won't haves  (not included, but maybe in the future some day)

Approved Feature/BugFix-requests usually get associated with 'promises', this is a big danger.

<br>
> **"The more heads, the more thoughts"**
> 
> This is a dutch expression, and it means that brainstorming can work counterproductive. A good
> startingpoint would be to let the leaddevelopers and CTO or one stakeholder take care of the
> 'end round' concerning this democratic process. More than 3 persons might introduce endless brainstorms.
> Make sure every employee has the opportunity to vote for a feature/issue. This will stop manipulation
> between collegues to push his/her agenda forward.
> A more strict approach would be the asian Kanban-method in which the developmentteam always reports
> an x amount of free slots for new issues/features.

### Possible examples ###

Ok, assuming that you somehow manage/log your features/bugs:

  * in an issue/bugtracker
  * a spreadsheet
  * a whiteboard
  * a kanban-style interface
  * in todo.txt 

### How to implement?

Bugtracker-users can add a 'M','S','C' or 'W' to their ticket-titles.
Or even better, a 'MoSCoW'-field to each ticket, it could look like this: &nbsp;&nbsp; **MoSCoW**: <select style="width:5.0em">
    <option value="">M</option>
    <option value="">S</option>
    <option value="">C</option>
    <option value="">W</option>
  </select>

Or, in case of a spreadsheet/textfile (personal projects eg.), here's what to do..suppose you have this list:

    1. [bug] fonts are too big on platform x, need size 12
    2. [feature] data needs to automatically do y
    3. [feature] data needs to automatically do y

If you communicate this to your staff/collegues, you could also do it like this:

    
    M. [bug] fonts are too big on platform x, need size 12
    C. [feature] data needs to automatically do y
    S. [feature] data needs to automatically do y

This is just an example, but it can be very powerfull as soon as you start using it right.

### Conclusion ###

RAD is great in certain situations, but if the software needs to be well managed, you better plan stuff.
I have no idea if I understood Steve Mcconnel's quote correctly, but in the above describe scenario he's right.
I also hope that I inspired many people with this.
Whether you are a (freelance) programmer, devteam, managementteam or stockholder: MoSCoW can be very effective.
I wish i had a timemachine; could go back in time; and hand over this article to myself..it would be such a productivity-booster!

### Further Reading ###

I think Steve Mcconnel probably has observed many different outcomes for many different projects, and that
many people can learn from him.
You probably want to read his [website](http://www.stevemcconnell.com/rdenum.htm).
He has many great advices which address many pittfalls for developmentteams. How could one ignore such free knowledge?

