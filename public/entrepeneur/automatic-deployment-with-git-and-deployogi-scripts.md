Automatic deployment with git and deployogi scripts 
===================================================

<br>

### Quote ###

> *Any code of your own that you havent looked at for six or more months might as well have been written by someone else.*
>
> -- quote by Eaglesons law 

### Case ###

How can a SaaS or App-company still deliver fast as the company matures?
How can they still deploy as if they were just a garage-startup with one programmer?

### What is deployment ###

Deployment is the process of getting a product live, up and running for the endusers.
As with every product, there is an implementationphase, and at some point it will become public.
Typical work to be involved is:

<img src="/custom/pages/blog/entrepeneur/res/deployment-source-destination.png" alt="deploying is not always easy as software matures"/>

* Uploading the code to another server (with slightly different configurations)
* Making sure the existing database works well with the upgraded code 
* Testing if everything works properly
* Security (these days are crazy)

As you can see, many things can go wrong here. Especially when dealing with deadlines.

### Background ###

As webapplication mature, features grow, codebase grows, team grows. But can a SaaS company still be able to deliver fast?
If you have one person doing all the deployment, then it means the deadlines become fully dependant on one employee, whatever teamwork 
was involved in an earlier stage. You definately want to prevent your team causing [this](/custom/pages/blog/entrepeneur/res/asleep-at-work.jpg) right?


### Solution: a deploymentmodel and a tool ###

To solve this, it can be handy to introduce a single deploymentmodel which multiple employees can understand- and/or execute (if they 
understand the matter). 
How can a devteam do this?, well they need to comply with the following checklist.

### The sane webdevteam checklist ###

* devteam should use subversioning like `svn` or `GIT`
* devteam should only deal with portable,buildable,(CLI)configurable webapplications (install/run anywhere)
* devteam should not allow writing features without (unit- or black/white/graybox)tests
* devteam should have seperation between programmers: developers (features) and maintainers (deployers)
* devteam should have a development, staging- and a production-server
* maintainers should use the same deploymenttool (git/svn is not a deploymenttool)
* the staging-server should contain a 'clone' of the production-server 
* devteam should be able to push to the staging-server (to see what happens), as if they were pushing to the production-server

### The tool: deployogi ###

Deployogi is a tool which turns many handhacking headaches into a laidback session.
Please pass this link to your devteam:

[The website of deployogi](https://github.com/coderofsalvation/deployogi)

> `NOTE`: there are tools out there which claim to deploy using git, however I was unfortunate to find any single tool which was also dealing with incremental 
> upgrades of complex webapplications 
> (usersubmitted data, upgrading/comparing of databases, different permissionschemes of filesystem e.g.)

As you can see on the website, incremental and modular upgrades is what deployogi focuses on: what could cost many many days/weeks/bugs if done manually:

<img src="https://dl.dropboxusercontent.com/s/88zzcgb4hp9k641/seqdiagram-deployogi-easy.png?dl=1"/>

### The big picture ###

At some point I wanted to come up with a deploymentmodel (as described earlier) for my current company which will put the focus more on delivering new features to endusers, instead
 of having the development cluttered up at deployment. 
 In case you are not frightened by more complex diagrams, you might wanna check out this full [deploymentmodel using deployogi](https://www.dropbox.com/s/rsa8w1wo3l80vao/seqdiagram-deployogi-scary.png?dl=1)
