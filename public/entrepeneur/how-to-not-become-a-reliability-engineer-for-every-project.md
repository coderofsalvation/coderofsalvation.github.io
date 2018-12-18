How to not become a reliability engineer
========================================

<br>
<img align="right" src="/data/upload/images/comic/out/comic_userfoo.jpg"/>

### Quote ###

> *Chuck Norris writes code that optimizes itself*
>
> -- quote by unknown

### The issue ###

Many people can have many ideas, which can result in many seperate webprojects with seperate timelines.
However, usually the first person who 'pushes' the code to the productionserver, ends up being mainly responsible for it. It might not always look like this from the beginning, but it usually ends up like this.

### Solution ###

Make sure that you dont start a webproject alone, and prepare the applicationskeleton so that 
other developers can code, deploy and take responsibility for the system.

### The 17 applicationskeleton commandments of the Coder of Salvation ###

From important to less important:

  1. use git and/or github
  1. automate repeated processes, write build-, test-, import- and export-scripts
  1. build cli commands which facilitate repetitive tasks (configuring configuration files)
  1. errors and uncaught exceptions should cascade into these logs
  1. design the skeleton so that developers can write plugins
  1. every plugin has a configurationfile containing at least the maintainer(s) emailadresses + phonenumbers 
  1. every plugin has a README.md file which briefly describes the usage,functionality and caveats.
  1. every plugin has a cronjob file
  1. every plugin has the ability to easily store/retrieve variables to a (json) file or database
  1. every plugin should have access to an centralized logging, and stdout function (no direct printing of output)
  1. the application should include a regressiontest framework like PHPUnit or testosteron(e) 
  1. if tests tail, deployment will be refused
  1. code should mention issuenumbers which reference to a issue/bugtracker
  1. let the application generate documentation
  1. document/provide at least some sequencediagrams to show the vital workflows
  1. provide/use a codingconvention / code documentation- and example- snippets/plugins
  1. always redirect emails to the issue/bugtracker
  1. distinguish between user/developer notifications, warnings, hard- and soft errors
  1. soft errors which dont halt the execution of plugin, hard errors do
  1. hard errors and uncaught exceptions should result in emails and/or sms depending on the plugin

### Now what? ###

Well, now upload the applicationskeleton to the liveserver, and put also a bare gitrepo on that server.
Let the bare gitrepo listen to the 'hooks/post-receive'-call, by triggering an automatic deployment to a webdirectory.
Now other developers (or just one) can push to this bare gitrepo, which triggers deployment.
The key is to not let it deploy when the tests are failing.
This is described in more detail in my other article [automatic-deployment-with-git-deployogi](/blog/automatic-deployment-with-git-and-deployogi-scripts).

> design the automatic deployment in a way that allows others to push plugins and/or together
> with the whole applicationskeleton (based on your desires).

### What kind of integrationtests should be the minimum? ###

The following tests should be passed before something would be deployed to live:

  * scan if all plugins pass a basic syntaxcheck
  * scan in pluginconfigs for developer emails (and phonenumber for sms)
  * scan whether none of the plugins contain functions longer than X lines (to prevent hacking)
  * scan whether none of the plugins contain exit- or die-calls which abort execution (and fail test if found)


### Then, if everything is set.. ###  

If you arranged all of the above or find a framework which does it for you: congratulations!
Now you can let developers push code, and become responsible for it.

`Disclaimer: the above guidelines are matching my taste, other configurations are also possible.` 
