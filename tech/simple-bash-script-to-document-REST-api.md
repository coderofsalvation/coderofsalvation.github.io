Bashscript to document REST api
===============================

### Problem ###

Sometimes projects are too tiny for fullblown offline docgenerators (doxygen/phpdoc(tor)) or online services like
(I/O mashable or Apigee).

### Solution ###

I was in a creative mood..and made this shellscript which scans php-files for certain REST-related commenttags, and turns it into html.

  * <a href="http://pastie.org/5657190" target="_blank">example input</a>
  * <a href="http://pastehtml.com/view/cojjnz16l.html"> example output</a>

It's kind of a minimalist startingpoint to get *any* type of custom documentation generated from
sourcecode.

### Conclusion ###

Definately a quickndirty one, but it works for me at least.
Its really easy to create/generate/update REST-documentation like this.
All information is a central place: the sourcecode.
Also its easy to create a pdf-handout for this: just rightclick in your browser -> print -> toPDF.
Just keep it in mind as a handy script to include in your doc/buildchain.

### Download ###

  * <a href="https://gist.github.com/4496972" target="_blank">here</a>

