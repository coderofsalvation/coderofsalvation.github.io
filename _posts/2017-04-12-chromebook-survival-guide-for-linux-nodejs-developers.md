---
layout: post
title: Chromebook survival guide for linux nodejs developers 
---

<div class="message">
  Hi! In this post I'm discussing my experiences with the acer chromebook 14 as a developer.
</div>

<img src="/public/img/chromebook.jpg"/>

## Why did i move to chromebook?

Well, basically curiosity, and my quest for:

<img src="/public/img/simplicity.png"/>

* I work with google chrome 24/7 
* I would love using it 12hr without power 
* I wanted an easypeasy stable linux environment with minimal gui
* I prefer letting the Chromium/Google-team take care of updates/security etc.

But most importantly:

* In the last years i found myself spending most of my time with terminal/websites/webapps/android apps

> I googled/youtubed people who were running dockers and ubuntu in a chroot, so i figured there's plenty room for desktop apps if needed.

## This took me 5 mins after I got my chromebook:

* put the chromebook in developer mode
* i bought a tiny 64GB pendrive for crouton chroot-backups and large files 
* i installed my dotfiles,vim, and nvm in my ubuntu xenial chroot created by [crouton](https://github.com/dnschneid/crouton)

Ok..it wasn't exactly 5 minutes ;)

> Boom! I was amazed to see that I could continue working on my projects already! 

After some days:

![](/public/img/chromebookshot.png)

## What did i tweak after receiving my acer chromebook 14?

* I installed [this beautiful terminal font & colors-scheme](https://gist.github.com/coderofsalvation/72c0b0b7d3288ab3748cf96629d08e81)
* I figured out how to [set terminal titles as tab titles](https://gist.github.com/coderofsalvation/8eef0f99a5a85e00f2c2da5b9e09292d)

## What i love so far

* the desktop environment is very minimal, smooth and slick
* alt-shift-m: the filemanager is pretty nice, and allows adding cloudstorage integration (i have a 1TB webdav STACK-account at transip)
* ctrl-shift-F5/cascade: take screenshot region to paste into slack
* shift-search-l: suspend laptop without closing the lid
* most important keyboard shortcut: CTRL-ALT-? (shows all shortcuts)
* extension: [nimbus screencapture](https://chrome.google.com/webstore/detail/nimbus-screenshot-screen/bpconcjcammlapcogcnnelfmaeghhagj?utm_source=chrome-app-launcher-search) easy peasy screencasts to paste into slack
* extension: the great suspender (never get out of tabs)
* the microphone: recording screencasts works very well out of the box, also in crouton/X11
* the speaker: very clean, clear loud sound
* switching linux/chrome desktop: ctrl-shift-f1 and ctrl-shift-f2 switches desktops backward/forward (f1=backward & f2=forward key)

## What I tried/used to use, but abandoned

| What | Why |
|-|-|
| [chromebrew](https://github.com/skycocker/chromebrew) | Eventhough it worked pretty well, I prefer [crouton](https://github.com/dnschneid/crouton) since it runs in it's own directory, rather than trying to mix software into Google's local OS.|
|tmux | I had some copy/paste issues, so I went for a lean-and-mean CTRL-ALT-T (opens terminaltab) + fullscreen-button approach. CTRL-1..9 allows me to switch terminals |
|linux desktop applications | eventhough LXDE/XFCE/KDE etc was easy to install using crouton, i didn't find myself needing it. In some rare cases i still can run GIMP or blender, but the usual image-editing tasks (rotate/crop/resize) can be done using imageviewer of chromeos's filemanager. I found `jwm` (Joe's windowmanager) a far better choice compared to LXDE/XFCE/KDE etc, since i don't need a second full-fledged windowmanager next to the awesome Chromeos.

## What I didn't try yet

[running docker using RKT](http://blog.vantol.org/running-docker-containers-on-a-chromebook-with-rkt/)

## Aliases 

Im using these alias in my `~/.bashrc` for crosh:

    alias ubuntu="sudo enter-chroot"
    alias startx="sudo enter-chroot xinit"
    alias enable_playstore="sudo bash ~/Downloads/enable_playstore"
    # cpu-friendly cp for big files
    alias cp="bash ~/Downloads/cp.sh"

## Vim tweaks 

Some chrome-shortcuts (Ctrl-w) conflicted with my VIM settings.
Therefore i made these changes to `~/vim/vimrc`, to make things comfortable:

		" chromebook fix: crouton/ubuntu hints vim to use latin
		set encoding=utf8

		" chromebook: switch windows with alt-arrowkeys instead of ctrl-w
		nmap \ <C-w>w
		nmap \| :tabnew:<CR> 
		nmap [ :tabp<CR>
		nmap ] :tabn<CR>

		" save on ctrl-s
		noremap <silent> <C-S>          :update<CR>
		vnoremap <silent> <C-S>         <C-C>:update<CR>
		inoremap <silent> <C-S>         <C-O>:update<CR>

> ctrl-w (switch buffer) became a dangerous shortcut, it abruptly closes the chrome tab including terminal and vim :D

## Tweak for transferring big files (prevents cpu hogs)

Sometimes I download movies from streaming moviesites (for travelling/offline purposes etc).
Somehow using `cp` caused cpu spikes (MMC storage related?), but i solved that with this script:

    #!/bin/bash
    # makes transferring big files cpu-friendly on chromebook
    #
    # usage:
    #
    #   put this script into ~/Downloads/cp.sh and put this in your ~/.bashrc :
    #
    #     alias cp='bash ~/Downloads/cp.sh'
    #
    [[ ! -n $1 ]] && { /bin/cp; exit 0; } 
    FILESIZE=$(( $( stat -c '%s' "$1" ) / 1024 / 1024 ))
    if [[ $FILESIZE -lt 50 ]]; then 
      /bin/cp "$@"
    else
      nice -n 20 ionice -c 3 /bin/cp "$@"
    fi

> Voila, this will automatically apply `nice` and `ionice` to the `cp` command (when files are bigger than 50MB). You could apply the same technique to other cpu-heavy commands.

HINT: also do this in your crouton chroots

## Middleclick paste for xterm on chromebook crouton X11 chroot

I rewired 'shift-backspace' to paste in xterm, by putting this script into `middleclick.sh`:

    #!/bin/bash
    xdotool mousedown --clearmodifiers 2
    xdotool mouseup 2
    xdotool keyup alt
    xdotool keyup ctrl
    xdotool keyup shift

And invoking it using this `.xbindkeysrc` file in my homedir:

    "/home/sqz/bin/middleclick"
        Shift + BackSpace 

## Running android apps

I was able to get android apps quickly up and running by putting this script in `Downloads/enable_playstore.sh`:

    #!/bin/bash
    if [[ $(whoami) == "root" ]]; then 
      #echo '--enable-arc' > /usr/local/chrome_dev.conf
      echo '--arc-availability=officially-supported' > /usr/local/chrome_dev.conf
      mount -o bind /usr/local/chrome_dev.conf /etc/chrome_dev.conf
      echo now press ctrl-shift-qq and the playstore should show up
    else 
      echo "must be root"
    fi

I didn't make this a permanent change, as i would like the OS to keep receiving its updates.
Also, most applications i use on android, also have a web- or chrome app variant (skype etc).
