Shellscripting the fast way
===========================

### Statement ###

*Shellscript allows you to mashup all programminglanguages at once, so learning it `as a swiss armyknife` really pays off in the longterm*

Especially when developing with vim or emacs, the testing/implementing-cycle is really fast, since you
can execute shellscripts from the editor itself.

### Why a framework is handy ###

Check out the minimal shellscript framework below, which I found to be very very productive.
It was inspired by [monkeytail](https://github.com/lmartinking/monkey-tail)
After developing a bit with it, I discovered the snippet below is an extract of its magic.


    #!/bin/bash
    
    _usage(){
        grep "^[^_].\+(){$" $0 | while read line; do 
          echo "  $0 $line" | sed "s/().*//g"; 
        done; 
        echo "";
    }
    
    foo(){
      echo "executing foo!"
    }
    
    # run arguments as commands if any, or show Usage
    "$@"
    if [ ${#1} == 0 ]; then echo "$CMDS" | echo "Usage: "; _usage; fi

### Explanation ###

Ok, basically you have private functions (starting with an underscore) and public functions. 
The script will list the available public functions (which are commands) by default (if no argument is given).
So on the commandline you can do:


    $ chmod 755 myshellscript 
    $ ./myshellscript 
      
      Usage:
        myshellscript foo
    
    $ myshellscript foo
    executing foo!

### Nitro inside your editor ###

Shellscripts turns vim/emacs/etc into a IDE without any problems. 
For example, in vim you can do:


    :!./%          <-- runs current script as external command 
      
      Usage:
        myshellscript foo

    :!./% foo
    executing foo!
    :!man curl     <-- gives manual about curl command 
    :!read --help  <-- gives manual about read command

### Fast workflow ###

The development workflow mentioned above can really improve your productivity. 
The shellscript language can be very picky about spaces and ';' signs, but it 
really pays off when you get the hang of it, and start using functions. 
You can start mixing all languages right away: 

    examplemix(){
      local msg=$1
      local foo=$(perl -e "$msg"); 
      local bar=$(php -r "echo md5('$msg');")
    }

    example "this is a message"

<br>
> **Demo:**
> 
> <div><script id="playterm-MjAxMi0wNi9jb2RlbWFzaHVwdHR5cmVjLTEzMzg1NDE2Nzl8ODB4MjQ=" type="text/javascript" src="http://playterm.org/js/?hash=MjAxMi0wNi9jb2RlbWFzaHVwdHR5cmVjLTEzMzg1NDE2Nzl8ODB4MjQ=" class="size:80x24"></script></div><br>
> 



### Automatic documentation ###

We could also extend our framework with autodocumentation.
In the following example we supply a comment for every funtion, and a
modified \_usage() function.


    # this will echo 'hello world'
    foo(){
      echo "hello world"
    }

    _usage(){
      grep "^[^_].\+(){$" $0 | while read line; do
        local cmd=$(echo "$line" | sed "s/(){//g")
        local info=$(grep -C0 -A0 -B1 "$cmd(){" $0 | sed "N;s/\n.*//g" )
        printf "    $0 %-20s %-40s\n" "$cmd" "$info" | grep "#"
      done; echo "";
    }

### Output ###


    $ ./myshellscript
      Usage:

        ./myshellscript foo         # this will echo 'hello world'

### Check requirements ###

It would be sad if people get all excited about a shellscript, to find out it doesnt
work on their system. Therefore, lets be very serious about it in advance.
Lets check if our commands are available like this: 


    requirements="sed grep printf cut sort php echo clear"

    ...

    checkrequirements(){
      for req in $requirements; do
        hash "$req" 2>&-
        if [ $? == 1 ]; then echo "please install '$req'"; exit; fi
      done;
    }

### Embed a manpage ###

To really top it off, lets add a manual (manpage) to really make it comfortable.
(Note: you could add 'pod2man' to the requirements-list mentioned above)
Also note the extended maincode on the bottom (before the manual).


    (code)

    manual(){
      if [ "$1" != "--manual" ]; then return 0; fi
      local tempfile="/tmp/foo.1"
      hash pod2man 2>&-
      if [ $? == 1 ]; then echo "please install perl"; exit; fi
      SCRIPT=`readlink -f $0`
      echo "(please wait..)"
      pod2man $SCRIPT > "$tempfile"
      clear
      if [ -f "$tempfile" ]; then man "$tempfile"; rm "$tempfile"; fi
      exit 0
    }

    manual "$1" && test $# -lt 2 && checkrequirements && usage && exit 65
    "$@"
    exit 0

    <<=cut
    =head1 NAME

       foo - a great cmdline utility

    =head1 SYNOPSIS

       This utility demystifies the wonderfull world of ...

    =head1 DESCRIPTION

    It does x and y..

    =head1 SEE ALSO

    L<foo>, L<bar>

    =head1 LICENSE

    BSD License (so everybody can enjoy it)

    =head1 AUTHOR

    B<Y>our name

    =cut
 
### Conclusion ###

Shellscript rocks, is available on every \*NIX system, and it will never die.
I hereby take back all insults I did in the past about this language ;) 
An example of all methods mentioned above: <a href="https://gist.github.com/1916309" target="_blank">https://gist.github.com/1916309</a>

### Resources ###

  * on channel #bash (FREENODE IRC) there the gurus are
  * [http://wiki.bash-hackers.org](http://wiki.bash-hackers.org)
