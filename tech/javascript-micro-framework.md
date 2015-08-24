Javascript micro framework
==========================

### Challenge ###

Find out what are actually the most necessary functionalities I need in a framework.

### Result ###

<pre style="white-space:pre">
    /**  MICRO FRAMEWORK BY THE CODER OF SALVATION (http://leon.vankammen.eu)
    /**/ var tplVars  = {}
    /**/ var ajax     = (navigator.appName == 'Microsoft Internet Explorer') ? new ActiveXObject('Microsoft.XMLHTTP') : ro = new XMLHttpRequest();
    /**/ function assign( varname, value )  { tplVars[ varname ] = value; }
    /**/ function fetch( content )          { for( key in tplVars ){ reg = new RegExp( "\\{\\$"+key+"\\}", 'g' ); content = content.replace( reg, this.tplVars[key] ); } reg = new RegExp( "\\{\\$[A-Za-z0-9_-]*\\}", 'g' ); content = content.replace( reg, "" ); return content; }
    /**/ function $( id )                   { return document.getElementById( id ); }
    /**/ function $_GET( name, url )        { name = name.replace(/[\[]/,"\\\[").replace(/[\]]/,"\\\]"); var regexS = "[\\?&]"+name+"=([^&#]*)"; var regex = new RegExp( regexS ); var results = regex.exec( url ? url : window.location.href ); if( results == null ) return ""; else return results[1]; }
    /**/ function get( url, id )            { ajax.open( 'get', url, true);     ajax.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');  ajax.onreadystatechange = function(){    if( ajax.readyState == 4 ){      var target = $( id );      if( target.tagName == "INPUT" )        target.value = ajax.responseText;      else        target.innerHTML = ajax.responseText;    }  }  ajax.send();}
    /**/ function post( url, id, vars )     { ajax.open( 'post', url, true);     ajax.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');  ajax.onreadystatechange = function(){    if( ajax.readyState == 4 ){      var target = $( id );      if( target.tagName == "INPUT" )        target.value = ajax.responseText;      else        target.innerHTML = ajax.responseText;    }  }  ajax.send( escape(vars) );}
</pre>

### Uses ###

  * Many things can be used in many ways
  * Prototype Selectors : `$('someid')`
  * Smarty-ish template engine : `smarty-like assign() and fetch() functions`
  * $_GET variabele : `similar to PHP`
  * post() : will post a form, and show the output in another DOM-element
  * get() : simple ajax-get request, and shows output in another DOM-element

### Tested ###

  * IE6
  * IE7
  * Firefox
  * Opera
