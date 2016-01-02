Switch between coffee- and javascript in vim like a ninja
=========================================================

## Problem

Coffeescript is for me, but not for everybody.

## Solution 

Code coffeescript, speak/commit javascript 

## How

I love to cheat with coffeescript while coding native javascript on linux.
Here's how I swap between pretty easily:

* run this once `npm install -g js2coffee coffee-script` 
* put this in your `vimrc`:

.

    nmap cc :! [[ \! -f %:r.coffee ]] && js2coffee % > %:r.coffee<CR>:sp %:r.coffee<CR>                                                                          
    nmap c> ggVG:!js2coffee<CR>
    nmap c< ggVG:!coffee --no-header -b -p -s<CR> 


* open a __.js__-file, and create/switch-to the `.coffee`-file by typing: `cc`
* convert any javascript buffer to coffeescript by typing: `c` `>`
* convert any coffeescript buffer to javascript by typing: `c` `<`

## My thoughts 

This is awesome.
Also check out the vim plugin for coffeescript](https://github.com/kchmck/vim-coffee-script).
The `:CoffeeWatch` command is pretty handy.
