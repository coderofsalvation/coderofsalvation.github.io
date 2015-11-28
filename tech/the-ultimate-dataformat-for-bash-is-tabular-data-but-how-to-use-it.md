The ultimate dataformat for Bash: tab,space, and comma seperated? But how?
==========================================================================

### Problem ###

I wish there was a textformat which enables me to share data between many programminglanguages *including* bash.

### Why ###

Because I want to use data from other sources (spreadsheets, applications etc).

### Solution: Tabular data (SSV/TSV/CSV) 

Tabular tabledata is easy to manage in bash (and if not, awk does).
Space separated values (SSV) is natively supported by bash:

    echo "one two three" | while read a b c; do
      echo $a,$b,$c
    done 

    # outputs: one,two,three

`TSV` works fine too when the field separator (Default:space) is changed to tabs:

    echo -e "one\ttwo\tthree" | while IFS=$'\t' read a b c; do 
      echo $a,$b,$c
    done

`CSV` works fine with gnu awk, which is installed on most systems:

<script src="https://gist.github.com/coderofsalvation/466d7da29a89980399b4.js"></script>

    cat foo.csv | csvget 1 3 

> NOTE: my personal favorite is csv since because of its import/export feature in spreadsheet editors.

### Conversion between TSV, CSV, and SSV

`from TSV to SSV`

    $ echo -e "foo\tbar" | expand 

`from SSV to TSV`

    $ echo "foo bar" | unexpand

`from CSV to TSV` 

<script src="https://gist.github.com/coderofsalvation/34a8350b5aaf1516cc21.js"></script>    

### Bonus: nice output in the console

CSV,TSV,SSV can look messy very easily:

    $ cat foo.csv
    status,tag,description,history,date
    BACKLOG,"","emailtemplate: layout optimize","",
    DONE,notifs,"emailtemplate: cancel subscription abstract workflow thru sb? (yes!)","",
    BACKLOG,notcus,"improved error logging (using log function) + errorscreen","",

Well, this looks better:

    $ cat foo.csv | csv2table
    13   BACKLOG    webapp             transfer paypal to bank        
    221  BACKLOG                       dd variable filters+digest payed 
    58   BACKLOG    bshlive            bshlive openshift (php webpipes 

<script src="https://gist.github.com/coderofsalvation/5c6c7e9b14ff7cdd49e9.js"></script>

### Other ideas: mashup with other languages

<style type="text/css">.gist { width: 523px; }</style>
<script src="https://gist.github.com/coderofsalvation/6120678.js"></script>
<br>
<script src="https://gist.github.com/coderofsalvation/48bade85bc09dd9e7ffd.js"></script>
<br>
<script src="https://gist.github.com/coderofsalvation/6120853.js"></script>

### Conclusion ###

Bash is ready for it, are you?
