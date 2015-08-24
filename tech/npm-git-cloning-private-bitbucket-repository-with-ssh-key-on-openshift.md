npm git cloning private bitbucket repository with ssh key on openshift
======================================================================

*Simple approach on using alternate ssh-keys to use with private repositories on openshift*

## The problem 

<br>

* an openshift application does not have a .ssh folder
* nor can it be created
* therefore, it can be created in the $OPENSHIFT\_DATA\_DIR directory
* but how to let git- or npm use this directory (and its keys) ?

## Solution step #1: generate an sshkey!

login to your openshift application ('foo' e.g.)

    $ rhc ssh foo

go to the data dir and create an ssh-key like so:

    $ cd $OPENSHIFT_DATA_DIR
    $ pwd
    /var/lib/openshift/3cc000b8e/app-root/data
    $ ssh-keygen
    Generating public/private rsa key pair.
    Enter file in which to save the key (/var/lib/openshift/54228f2a5973ca43cc000b8e/.ssh/id_rsa): /var/lib/openshift/3cc000b8e/app-root/data/id_rsa
    (enter..enter..enter..)

> Make sure you enter the right directory in the 'Enter file in which..'-prompt (hence the 'pwd' command)

## Solution step #2: an ssh wrapper!

Now lets create an ssh wrapper:

    $ cd $OPENSHIFT_DATA_DIR
    $ echo 'ssh -t -o "StrictHostKeyChecking no" -i $OPENSHIFT_DATA_DIR/id_rsa "$1" "$2"' > sshwrapper
    $ chmod 755 sshwrapper

Then run this (just to test, or in your deployscript):

    GIT_SSH=$OPENSHIFT_DATA_DIR/sshwrapper npm install git+ssh://git@bitbucket.org:yourname/yourrepo.git
    GIT_SSH=$OPENSHIFT_DATA_DIR/sshwrapper npm update  git+ssh://git@bitbucket.org:yourname/yourrepo.git

or simply:

    $OPENSHIFT_DATA_DIR/sshwrapper clone ssh://git@bitbucket.org:yourname/yourrepo.git

Voila! This should work.
If not, please revise the steps above, or comment below.

## In retrospect

The 'StrictHostKeyChecking no' option was passed, to enable automatic deployments (or calls from .openshift/action_hooks/deploy hook).
