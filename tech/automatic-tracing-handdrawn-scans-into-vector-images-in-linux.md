Tracing handdrawn scans
=======================

<img src="/data/upload/images/comic/out/comic_pencilrules.jpg" width="100%"/>

Ever wanted a quick simple way to convert your handdrawn scans into something fancy?

### Problem ###

  * Handdrawn scans introduce colorproblems
  * Its hard to hint the computer to curve stuff smoothly
  * Black and white (marker) drawings are hard to convert to black/white pixels
  * Perfect scaling..How to get from pixels to vectors?
  * Scanned handdrawn comics are not easily converted to digital comics

### Input Format ###

Just a scan of your handdrawing, almost any format will work.

### Output Formats ###

  * EPS (.eps)
  * POSTSCRIPT (.ps)
  * PDF (.pdf)
  * Standard Vector Graphic (.svg)
  * Drawing Interchange Format (.dxf)
  * Portable Greymap (.pgm)
  * GimpPath (.svg)
  * Xfig (.xfig)

### Requirements ###

You need a linux system with the following packages:

  * imagemagick convert
  * potrace 

### Examples ###

Before:

<img src="/data/upload/images/comic/tag_1.jpg" width="400"/>

Commandline:

    /comicize tag_1.jpg tag_1_out.jpg "tag 1" 600 1 100 20 1

<img src="/data/upload/images/comic/out/tag_1_out.jpg" width="400"/>

Before:

<img src="/data/upload/images/comic/tag_2.jpg" width="400"/>

Commandline:

    /comicize tag_2.jpg tag_2_out.jpg "tag 2" 600 1 100 20 1

<img src="/data/upload/images/comic/out/tag_2_out.jpg" width="400"/>

### Notes ###

I included the last picture to point out, that sometimes one needs to fiddle with the settings.
In any case, the better the picture, the less you have to fiddle.

### Downloads ###

Install the script below like this:

    $ wget "https://raw.github.com/gist/4261783/f45be51919e11fb93dfb0f6dabb6d404a1400bc5/comicize" -O comicize
    $ chmod 755 comicize

<script src="https://gist.github.com/4261783.js?file=comicize"></script>
