Actionscript cpu hogs
=====================

Sometimes investigating a problem is the problem itself.
Last night I was dealing with strange slowdown in my animations.<br>
I started tracing more stuff, and in the end it turned out the tracing was the problem :)<br>

### Tracing + Animation = Bad Idea ###

Conclusion: Avoid tracing raw objects within tight animation code.

### Problemcode ###

    public function replaceSide( source:DisplayObject, 
                                 replacement:DisplayObject 
                               ) : void {
      Util._trace("6) time = "+getTimer() );
      var side:Array = [ sideFront, sideRight, 
                         sideBack , sideLeft, 
                         sideTop  , sideBottom ];
      Util._trace("7) time = "+getTimer() );
      var obj:Array  = [ objFront, objRight, 
                         objBack , objLeft, 
                         objTop  , objBottom ];
      Util._trace("8) time = "+getTimer() );
      Util._trace("trying to replace");
      Util._trace( source );
      Util._trace( "with" );
      Util._trace( replacement );
      Util._trace("9) time = "+getTimer() );
      for( var i:int = 0; i < obj.length; i++ ){
        if( obj[i] == source ){
          side[i].removeChild( obj[i] );
          side[i].addChild( replacement );
          replacement.x = obj[i].x;
          replacement.y = obj[i].y;
          replacement.z = obj[i].z;
          if( obj[i] == objFront )  objFront  = replacement;
          if( obj[i] == objRight )  objRight  = replacement;
          if( obj[i] == objBack )   objBack   = replacement;
          if( obj[i] == objLeft )   objLeft   = replacement;
          if( obj[i] == objTop )    objTop    = replacement;
          if( obj[i] == objBottom ) objBottom = replacement;
        }
      }
      Util._trace("10) time = "+getTimer() );
    }

### Profiling data ###    

    7) time = 43656
    8) time = 43657
    trying to replace
    [object VideoPlayer]
    with
    [object VideoPlayer]
    9) time = 44780
    10) time = 44792

Did you noticed when I traced the DisplayObjects, it costed about 23 ms? This
caused a hickup in my animation.
This trace was there all along before the bughunt, so when I removed them
everything was fine.

