---
layout: post
title: Chromebook survival guide for linux nodejs developers 
---

<div class="message">
  Hi! In this post I'm discussing my experiences after leaving years of linux/windows distros behind, after buying an acer chromebook 14.
</div>

<img src="/public/img/chromebook.jpg"/>

## Why did i move to chromebook?

Well, basically to ensure productivity and:

<img src="/public/img/simplicity.jpg">

* I love google chrome + working 12hr without power 
* I wanted an easypeasy stable linux environment with minimal gui
* I prefer letting the Chromium/Google-team take care of updates/security etc.
* Simplify my workflow

Basically i want to spend less time on configuring non-trivial linux-stuff. Linux desktops/windowmanagers are fun, dangerously fun (to keep tinkering with).
But most importantly:

* I mostly use terminal/websites/webapps/android apps anyways

> I googled/youtubed people who were running dockers and ubuntu in a chroot, so i figured there's plenty room for tinkering if needed.

## This took me 5 mins after I got my chromebook:

* put the chromebook in developer mode
* i bought a tiny 64GB pendrive to put my crouton chroots onto
* i installed my dotfiles,vim,nvm and nodejs in my ubuntu xenial chroot created by [crouton](https://github.com/dnschneid/crouton)

Ok..it wasn't exactly 5 minutes ;)

> Boom! I was amazed to see that I could continue working on my projects already! 

After some days:

![](/public/img/chromebookshot.png)

## What did i tweak after receiving my acer chromebook 14?

* I installed [this beautiful terminal font & colors-scheme](https://gist.github.com/coderofsalvation/72c0b0b7d3288ab3748cf96629d08e81)
* I figured out how to [set terminal titles as tab titles](https://gist.github.com/coderofsalvation/8eef0f99a5a85e00f2c2da5b9e09292d)
* I made mixcloud.com my musicplayer, and pinned it to the shelf to run in a window 

## What i love so far

* the desktop environment is very smooth, apple-like
* alt-shift-m: the filemanager is pretty nice, and allows adding cloudstorage integration (i have a 1TB webdav STACK-account at transip)
* ctrl-shift-F5/cascade: take screenshot region to paste into slack
* shift-search-l: suspend laptop without closing the lid
* most important keyboard shortcut: CTRL-ALT-? (shows all shortcuts)
* extension: [nimbus screencapture](https://chrome.google.com/webstore/detail/nimbus-screenshot-screen/bpconcjcammlapcogcnnelfmaeghhagj?utm_source=chrome-app-launcher-search) easy peasy screencasts to paste into slack
* extension: the great suspender (never get out of tabs)

## What I tried/used to use, but abandoned

| What | Why |
|-|-|
| [chromebrew](https://github.com/skycocker/chromebrew) | Eventhough it worked pretty well, I prefer [crouton](https://github.com/dnschneid/crouton) since it runs in it's own directory, rather than trying to mix software into Google's local OS.|
|tmux | I had some copy/paste issues, so I went for a lean-and-mean CTRL-ALT-T (opens terminaltab) + fullscreen-button approach. CTRL-1..9 allows me to switch terminals |
|linux desktop applications | eventhough LXDE/XFCE/KDE etc was easy to install using crouton, i didn't find myself needing it. In some rare cases i still use it to launch GIMP or blender, but imagemagick or the screenshot-region kb shortcut usually does the job most of the time.

## What I didn't try yet

[running docker using RKT](http://blog.vantol.org/running-docker-containers-on-a-chromebook-with-rkt/)

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

