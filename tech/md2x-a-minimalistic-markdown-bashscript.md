md2x
====

*Minimalist (markdown2html) converter*

### what is it ###

md2x is a `bashscript` which quickly turns your <a href="http://en.wikipedia.org/wiki/Markdown" target="_blank">Markdown</a>-document(s) into html5 webpages (or a miniblog/indexed site).

### Example ###

    $ md2x html input/foo.md 
    $ md2x htmlcss input/foo.md 
    $ md2x htmlcssindex inputdir outputdir

Actually, was website is generated 100% using md2x.

### Why ###

  * less distractive (`stay in the shell`)
  * nothing beats plain html (`it never crashes`)
  * asciidoc is a heavy toolchain (`many dependancies`)
  * browsers print to pdf these days
  * quickly generate docs/blogs for projects
  * New tag: easily embed external output : `{!ls -la}` (\*)
  * because we can

\* = it will become a literal block if 4 spaces occur before the tag

### Dependancies ###

  * GNU/Linux
  * awk
  * bash
  * sed

### Installation ###

Just copy paste this in the console:

    wget "http://leon.vankammen.eu/tech/res/md2x" && chmod 755 md2x
    wget "http://leon.vankammen.eu/tech/res/example.md"
    ./md2x htmlcss example.md

### Further hacking ###

    $ export HTML_BANNER="<img src='logo.png'/>"
    $ export HTML_FOOTER="<img src='http://creativecommons.org/licenses/by-nc-nd/3.0/deed.en_US'/>"
    $ md2x htmlcssindex somedir

### Additional Credits ###

  * Jesus Galan (yiyus) 2009

