Githooks the minimist quality assurance tool
============================================

## Problem

* You want to prevent broken commits
* You want to prevent pushing unwanted debug-code
* You want to prevent pushing outdated documentation 
* You want to proofread your code before pushing

How to automate your workflow with these concerns?

### Solution: githook

Sure, there are zillions of quality assurance tools out there, and they're great.
But sometimes a teaspoon a bash and one slice of githook will do as well.

<center><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e0/Git-logo.svg/2000px-Git-logo.svg.png" width="50%"/></center>

## Example

This simple approach worked well for me so far:

    $ git commit -m "foo"
    update + add version in README.md
    generate docs (y/n) ? n
    checking debug calls..
    client.js:345+ trace "fooo"
    continue (y/n)? y
    scanning for forbidden calls ( process.exit() / die() etc) ....none found
    running tests?...no because branch != master
    commit finally? (y/n) y
    $ git push origin master

It basically automates all the steps 

## Instructions

    $ mv .git/hooks .hooks 
    $ cd .git && ln -s ../.hooks hooks && cd - 
    $ ls -la .git/
    drwxr-xr-x  5 sqz sqz 4.0K Oct  7 10:31 ..
    drwxr-xr-x  7 sqz sqz 4.0K Oct  7 10:31 .
    drwxr-xr-x 25 sqz sqz 4.0K Oct  7 10:31 objects
    drwxr-xr-x  3 sqz sqz 4.0K Oct  5 13:52 logs
    drwxr-xr-x  5 sqz sqz 4.0K Oct  5 13:52 refs
    drwxr-xr-x  2 sqz sqz 4.0K Oct  5 13:52 branches
    drwxr-xr-x  2 sqz sqz 4.0K Oct  5 13:52 info
    -rw-r--r--  1 sqz sqz 1.2K Oct  7 10:31 index
    lrwxrwxrwx  1 sqz sqz    9 Oct  7 10:31 hooks -> ../.hooks    <-----------------------
    -rw-r--r--  1 sqz sqz   16 Oct  5 13:59 COMMIT_EDITMSG
    -rwxr--r--  1 sqz sqz  239 Oct  5 13:54 config
    -rw-r--r--  1 sqz sqz  117 Oct  5 13:52 FETCH_HEAD
    -rw-r--r--  1 sqz sqz   73 Oct  5 13:52 description
    -rw-r--r--  1 sqz sqz   23 Oct  5 13:52 HEAD
    $ mv .hooks/pre-commit{.sample,}
    $ vi .hooks/pre-commit
    ( edit the hook and call other scripts e.g. but remember the script needs to exit with exitcode 0 to do the actual commit )
    $ git add .hooks && git commit -m "added hooks"$

Voila! Now you have repo-specific hooks which are easily extenable.

## Server specific actions on pull

Similar things can be done on a (live)server with the `hooks/post-update` hook, for example:

    [[ $(</etc/hostname) == "liveserver" && $branch != "master" ]] && { echo "only master branch on liveserver, aborting.."; exit 1; }
    [[ -x patches/$commit.php ]] && patches/$commit.php

> I am aware of phrases like "git is not a deployment tool", "never use root", "bash is dangerous" and other totalitarian expressions parrotted around the web.
> However I'm more a proponent of "many things can be done in many ways", and "learn your tools/languages"
> Actually I would recommend distrusting anybody who promotes one way of doing things.

## More Githook Tips

For more inspiration see [here](http://codeinthehole.com/writing/tips-for-using-a-git-pre-commit-hook/)
