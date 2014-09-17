---
layout: default
title: Deploying node-red on openshift
---

<iframe src="//player.vimeo.com/video/26532298" width="100%" height="500" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe> <p><a href="http://vimeo.com/26532298">Starting with everyauth</a> from <a href="http://vimeo.com/pedroteixeira">Pedro Teixeira</a> on <a href="https://vimeo.com">Vimeo</a>.</p>
<div class="message">
  Howdy! In this post I will explain how to deploy node-red easily to openshift.
</div>

### Why?

Openshift has awesome hook-features, but they exist *inside* the repo.
This is not always handy (think passwords e.g.), so a good option is to have
the deployscript sitting outside the repo.

### Getting started 

First being by logging in to your server using ssh:

    [your-yourapp.rhcloud.com 6cad7fd000041]\> cd app-root/data/

    [your-yourapp.rhcloud.com 6cad7fd000041]\> cd app-root/data/
    [your-yourapp.rhcloud.com data]\> ls -la
    total 32
    drwxr-x---. 4 5418 54183 4096 Sep 16 11:38 .
    drwxr-xr-x. 5 root 54183 4096 Sep 16 08:43 ..
    -rw-------. 1 5418 54183 1321 Sep 16 12:47 .bash_history
    -rwxr-x---. 1 5418 54183  116 Sep 16 08:43 .bash_profile
    -rwxr-xr-x. 1 5418 54183  543 Sep 16 10:34 deploy
    drwx------. 3 5418 54183 4096 Sep 16 10:11 lib
    drwxr-xr-x. 2 5418 54183 4096 Sep 16 08:44 .nodewatch
    -rwxr-x---. 1 5418 54183   80 Sep 16 08:43 .vimrc

This data-directory is nice, because it doesnt get erased during deployment.
Now make sure you have this 'deploy' file sitting in this directory:

    #!/bin/bash 
    # bit of bash-voodoo to massage our settings.js

    PROJECTDIR="$OPENSHIFT_HOMEDIR"app-root/runtime/repo
    DATADIR="$OPENSHIFT_HOMEDIR"app-root/data
    ADMIN_PW="yourpassword"

    cd "$PROJECTDIR"

    {
      echo "configuring admin credentials"
      pwmd5="$(echo -e "$ADMIN_PW\c" | md5sum )"
      pwmd5="${pwmd5:0:32}"
      sed -i 's/httpAdminAuth:.*/httpAdminAuth: {user:"admin",pass:"'$pwmd5'"},/g' settings.js

      echo "configuring user datadir"
      sed -i 's| .*userDir:.*|userDir: "'$DATADIR'",|g' settings.js
    } | while read line; do echo "[./app-root/data/deploy] $line"; done

Dont forget to run a 'chmod 755 deploy' on it.
Run it, test it, and finally commit the following changes to your repo:

    mkdir -p .openshift/action_hooks
    cd .openshift/action_hooks

Then put this file 'pre_build' in it:

    #!/bin/bash 
    deploy=$OPENSHIFT_HOMEDIR/app-root/data/deploy

    [[ ! -f "$deploy" ]] && { echo "$deploy was not found..aborting" && exit 0; }
    $deploy

Dont forget to run a 'chmod 755 deploy' on it.
Commit it, push it, and voila! 

### What happened here?

> Instead of storing passwords/deployscripts in the repo (not always a good idea), we let our hook call a script which is outside the repo.

