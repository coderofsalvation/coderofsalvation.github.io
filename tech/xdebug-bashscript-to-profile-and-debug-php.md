Xdebug console
==============

A bashscript which easifies PHP debugging/profiling on live and productionservers.

### Usage ###


    Usage: 
        xdebug start    [options] <phpfile> [args]   <- triggers xdebug session for Zend/Eclips/Vim 
        xdebug profile  [options] <phpfile> [args]   <- generates a .cg (cachegrind) profiler file 
        xdebug trace    [options] <phpfile> [args]   <- generates a fulltrace textfile of the phprun
        xdebug summarize  <yourfile.cg>              <- summarizes a .cg file as simple text output
    
    type 'xdebug --manual' to see the manual + examples

### Demo ###

Check out <a target="_blank" href="http://playterm.org/r/php-xdebug-in-console-1330338498">this</a> playterm recording.

### Download ###

<a href="https://gist.github.com/1916309" target="_blank">https://gist.github.com/1916309</a>
