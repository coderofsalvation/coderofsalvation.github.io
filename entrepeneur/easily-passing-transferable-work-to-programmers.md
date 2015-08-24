How to create transferable, mobile webprojects
==============================================

<br>
<img align="right" src="/data/upload/images/comic/out/comic_userfoo.jpg"/>

### Quote ###

> *Any code of your own that you havent looked at for six or more months might as well have been written by someone else.*
>
> -- quote by Eaglesons law 

### What is a transferable webproject ###

A transferable project which can easily picked up by a collegue developer, and radiates similarity in workflow compared to other projects.

### How to get similarity in projects ###

From important to less important:

  * see other programmers as yourself (empathy)
  * using the same issue/bugtracker to manage bugs/todos
  * using the same subversioning workflows (git/svn)
  * use the same codingconvention / code documentation snippets
  * always redirect emails to the issue/bugtracker
  * document howtos/workflows in the sourcetree or issue/bugtracker
  * try to work live on webservers, using vim/emacs or something else respectable
  * try to automate repeated processes, write build-, test-, import- and export-scripts
  * provide at least some sequencediagrams to show the vital workflows
  * focus on small function bodies
  * generate further documentation on your code (when a long livecycle is necessary).

`Disclaimer: the above guidelines are matching my taste, other configurations are also possible.` 

One might wonder why documentation is less important then the other aspects.
Well, it can be of great help, but documenting stuff is also like flossing: everybody agrees,
not many do it. 
Also, sometimes debuggingskills might come more in handy in case of urgent bugfixing.

### Obstacles ###

These things might interfere between collegues/projects:

  * several servers / passwords (for deployment etc)
  * filesystem permissions
  * incompatible massive-gui-editor projectfiles
  * programming too long alone on your project 
  * non-portable project-legacy, the project started from scratch and transformed into something mysterious.
  * exotic desktoptools which are necessary for building the application

### Solution: introduce a virtual college called 'foo' ###

Who is person foo?
Person foo is the virtual 'collegue'.
Many problems can be solved just by introducing an nonexisting collegue, who has its own:

  * own unix account (filesystem/permission/crons)
  * own email (issuetracker user)
  * own IRC/Facebook/etc-messenger-bot (for namedpipe-to-chat logging)
  * own dropbox
  * own google account (to sync issues to excel-spreadsheets online)

Many problems can be solved by running tasks under this username.

Example: *Person A installs a cron which generates reports, and or receives a lot of stats/important info exclusively in his mailbox. Person A quits the company. Nobody has any clue where to look for. This is unwanted extra work.*

Ok one can argue why somebody would do these activities, but the reality is that programmers are humans. Humans make misstakes, and usually each human 'knows/does something special' on the server(s).
Many problems can be solved by sharing the 'foo' emailbox, or running cronscripts under users-privileges foo.
Foo will never leave the company.

### Cream on the Cake ###

Run all team-related cronjobs by user 'foo' run.
A fully automated customized devserver can be hard to debug if everybody is running their own team-related crons.
Advicable is to write a monitorscript, run by user 'foo' crontab, which checks if all necessary processes actually run.
Imagine, collegue 'foo' is awake for 24 hours..and can always watch/assert things.
Isnt there something really powerfull in this?

### But what about PaaS? ###

In times of SaaS and PaaS it is not always possible to get away from IaaS.
Sometimes SaaS-projects are so specific, and need specific serverconfigurations.
In those cases it can pay off to introduce user 'foo' to those IaaS systems.

*User foo is always at your service, even when your collegues leave*
