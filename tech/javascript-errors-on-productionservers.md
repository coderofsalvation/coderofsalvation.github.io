Javascript on productionservers
===============================

### Problem ###

A client calls because the system is 'not workable'.
You check, but cannot find anything strange.
So, we enter the voodoo-area: it might be a specific  browserbug, temporary bug, etc.

### Conclusion ###

You don't want bugs which are not reproducable.

### Ideal situation ###

You discovered the bug, and tell the client it has already been
fixed as soon as he calls.

### Possible solution ###

Usage of:

  * PHP's error handlingmechanism (set_error_handler)
  * Javascript error handling mechanism (window.error)
  * sending of email

### Javascript Code ###

    //
    // 23-12-2009 Coder of Salvation start from scratch
    //
    var error = {
      url: "/error",
      ro:  (navigator.appName == 'Microsoft Internet Explorer') ?
            new ActiveXObject('Microsoft.XMLHTTP') : ro = new XMLHttpRequest(),
      init: function(){
        // assign own handler
        window.onerror = error.handleError;
      },
      /*
       * advanced: a full error handler
       */
      handleError: function(err, url, line) {
        var log = 'err='          +err+
                  '&amp;url='          +url+
                  '&amp;line='         +line+
                  '&amp;host='         +document.location.host+
                  '&amp;href='         +document.location.href+
                  '&amp;pathname='     +document.location.pathname+
                  '&amp;appCodeName='  +navigator.appCodeName+
                  '&amp;appName='      +navigator.appName+
                  '&amp;appVersion='   +navigator.appVersion+
                  '&amp;cookieEnabled='+navigator.cookieEnabled+
                  '&amp;platform='     +navigator.platform+
                  '&amp;userAgent='    +navigator.userAgent;
        error.ro.open( 'post', error.url , true);
        error.ro.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
        error.ro.send( log );
        return true; // error is handled
      }
    }
    error.init();

The above could be a good starting point, you might even want to wrap your whole code into an exception-block.
It might also be a good idea to see if your javascriptframework supports something similar.

### PHP Code ###

    // not tested, but good as a start
    ob_start();
    print_r( $_GET );
    $out = ob_get_contents();
    ob_end_clean();

    mail( "you@mail.com", "your subject (error)", $message );

