Switch between coffee- and javascript in vim like a ninja
=========================================================

## Problem

Coffeescript is not for everybody.

## Solution 

* _Code_ in coffeescript, _commit_ javascript 

## How

* Just write coffeescript in .js-files
* select the coffeescript
* convert it 

## How to code both..at the same time?

Install the tools using `npm install -g js2coffee coffee-script` 

> put this in your `vimrc`:

    " easy expansion to js (>) and compressing to coffeescript (<)
    vmap c< :!js2coffee<CR>
    vmap c> :!coffee --no-header -b -p -s<CR>
    nmap c< ggVG:!js2coffee<CR>
    nmap c> ggVG:!coffee --no-header -b -p -s<CR>:%s/};/};^M/g<CR> 
    nmap cc :! [[ \! -f %:r.coffee ]] && js2coffee % > %:r.coffee<CR>:sp %:r.coffee<CR>                                                                                                               
## Example: Selections 

> Selections are handy when you don't want `.coffee` files in your repo (*)

* open a __.js__-file, code some lines of coffeescript 
* now select those lines using `ctrl+shift+v` and `j` (arrow-down)
* press `c>` to convert the selection to javascript
* press `c<` to convert the selection to coffeescript 

* = eventhough [this](http://stackoverflow.com/questions/13645824/can-i-write-npm-package-in-coffeescript) is the adviced approach for modules, there are reasons to not want `.coffee`-files in your repo (clean commits).

## Example: switching / converting files

* recommended: open a __.js__-file, and create/jump-to the `.coffee`-file by typing: `cc`
* convert any javascript buffer to coffeescript by typing: `c` `>`
* convert any coffeescript buffer to javascript by typing: `c` `<`

## My thoughts 

This is awesome:

> think in coffeescript when editing a javascriptfile.

Also check out the vim plugin for coffeescript](https://github.com/kchmck/vim-coffee-script).
The `:CoffeeWatch` command is pretty handy.
