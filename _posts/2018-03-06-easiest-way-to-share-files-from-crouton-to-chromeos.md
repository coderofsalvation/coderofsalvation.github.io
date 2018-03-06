---
layout: post
title: Easiest way to share files from Crouton to Chromeos
---


<center>
  <img src="http://leon.vankammen.eu/public/img/sharing.svg" width="50%" style="max-height:400px"/>
</center> 

<div class="message">
  Hi! In this post I'm discussing the easiest way to share files of my Ubuntu crouton with Chromeos.
</div>

## The problem 

Files in my crouton home-folder are not exposed to Chromeos.
I want to be able to use Gimp, and use that file in my Chromeos or Android Apps.

## Solutions i tried

| Solution | Result |
|-|-|
| SSH mount using the chromeos file-manager | Cumbersome, also seemed buggy with some chromeos apps (Caret-T) |
| Put file in ~/Downloads folder | Cumbersome, and results in messy ~/Downloads. Temporary files get backed up by google (large videofiles etc) | 

## My favorite solution

* A usb stick!

Just put this in `/etc/rc.local' 

```
FOLDER=~/projects
for i in $FOLDER/*; do 
  mount --bind "$i" "/media/removable/USB Drive/$FOLDER/$(basename "$i")" 
done
```

## Explanation

* I have a `project`-folder in both my home-folder, and on my usb stick 
* The usb stick `project`-folder contains projects which im not actively working on (github checkouts/libraries etc)
* The `project`-folder in my home-directory contains projects im **actively working** on 
* During crouton initialization, it links the homefolder-projectdirs to my USBstick (using mount --bind)

Benefits:
* Chromeos can see the USB stick
* In case my usb stick dies, I'll only lose those (USB) projects which are not actively worked on

