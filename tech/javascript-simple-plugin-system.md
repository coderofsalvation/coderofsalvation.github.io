Javascript simple plugins
=========================

### Statement ###

*In an ideal world clients always know what they want, and programmers know how to design it.*

### Reality ###

Unfortunately, this isnt the case, especially if you're building something original from scratch.
Putting code into plugins is a great way of seperating feature-code from engine-code.

> NOTE: the code below probably will not compile out of the box since 
>       its a snippet of productioncode
>       ..but you'll get the idea
     

### youapp.js ###

    (function(){
      var yourapp = {
    
         init: function(){
           for( i in this.plugin ){
             this.plugin[i](this);
             _trace("plugin '"+i+"' registered succesfully");
           }
         }
      };
    })();


### plugin.rotate.js ###

    function reverseRotate(yourapp){
      var reverse = (yourapp.frames['@rotate'] != "right");
      _trace( yourapp.frames );
      if( reverse ) yourapp.frames = array_reverse(yourapp.frames);
      if( reverse ) _trace("reversing array");
      _trace( yourapp.frames );
    };
    yourapp.plugin['rotatedirection'] = function(yourapp){
      yourapp.event.addListener( "FRAMES_LOADED", reverseRotate );
    }

### Benefits ###

At a later point, you can always decide to integrate things in the engine, or to totally abandon a plugin.
Its a good strategy to have a placeholder for 'wild features', without introducing *codesmell* in your *core code*.
It makes programming new features fun, readable and maintainable.

### Personal note ###

I found out, that simple by refactoring the code everytime, this is not fun.
Its not fun to refactor the code everytime certain features are introduced.
So with 'never repeat yourself' in mind, I decided that postponing refactoring would be wise by using plugins.
Then at a later time I always can refactor the code at a moment I want, without having the burden of codesmell.
