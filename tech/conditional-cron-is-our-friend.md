Conditional Cron
================

### Problem ###

Cron is our friend, but only programmed to be loyal & faithfull.
In some cases we want cron to do something..and sometimes not (condition).

### Solution ###

Instead of writing/seperating crontasks, make one smart cronjob using the date-cmd.

### Example ###

    0 0 * * * /home/username/somecmdA >> .cron.log                                  
    0 1 * * * /home/username/somecmdB >> .cron.log                                  
    0 0 1 * * /home/username/somecmdC >> .cron.log      

What if all commands are doing the same stuff..seperation can be good and bad.

### Possible solution ###

    0 0 * * * /home/username/somecmd >> .cron.log                                  

and then in somecmd:

    # do common everyday stuff
    echo "doing everyday stuff"
    if [ $(date +%a) == "Tue" ] ; then cleanuplogs; fi  

### Demo ###

<br>
<div><script id="playterm-MjAxMS0wOS9jb25kaXRpb25hbGNyb250dHlyZWMtMTMxNzEyNDYyMHw4MHgyNA==" type="text/javascript" src="http://playterm.org/js/?hash=MjAxMS0wOS9jb25kaXRpb25hbGNyb250dHlyZWMtMTMxNzEyNDYyMHw4MHgyNA==" class="size:80x24"></script></div><br>

