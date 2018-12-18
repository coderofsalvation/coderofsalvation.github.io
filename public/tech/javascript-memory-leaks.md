Javascript memory leaks
=======================

Some tips for making applications which have to be able run all day.

### Rule of thumb ###

The deeper in the scope, the more likely the chance for memory leaks.

### What browser does for you ###

Many browsers do reference-counting as garbage-collection.
It means, if there are variables in memory which arent referenced by other variables, it will be deleted from memory.

### DOM object ###

DOM-variables as an argument creates memory leaks in many browsers, so try to do:

    function bla( idname ){
      $(idname).doSomething();
    }
 
instead of
 
    function bla( el ){
        el.doSomething();
    }

### But what about delete() and removeChild()? ###

They work fine in native javascript, but it will likely not work as soon as you work with proptotyped libraries/frameworks
(like jquery/mootools etc).
Therefore use empty() or destroy() or whatever your framework advices.

### Profiling ###

Profiling is the process of measuring time and memory concerning code.
Excellent tools to find memory leaks on the spot.

 
**Chrome**

It has builtin-tools, just press F12.

**Firebug**

a great one for firefox browser the bestfor firefox <a href="http://www.getfirebug.com" target="_blank">(Get it here)</a>

**Manual**

Optionally, one could write a for-loop which does something 500 times, and see
if the executiontime or memoryvalues grow in a strange way. (The following code 
has no guarantees and needs tweaking)

    var timer;
    var counter = 0;
    var maxCount = 20;
    var doSomethingResults;
    var iv;
    function intervalIt( outputId) {
      timer = new Date();
      var startTime = timer.getTime();
      for (var i = 0; i &lt; 500; i++)
      {
          doSomething();
      }
      timer = new Date();
      var endTime = timer.getTime();
      var output  = document.getElementById( outputId );
      output.innerHTML += "doSomething() :: "+(endTime-startTime);
      output.innerHTML += "&lt;br /&gt;";
      doSomethingResults += (endTime-startTime);
     
      if (counter &gt; maxCount) {
        clearInterval(iv);
        output.innerHTML += "doSomething()  Average: ";
        output.innerHTML += "(doSomethingResults/maxCount);
        output.innerHTML += "&lt;br /&gt;";
      }
      counter++;
    }

### Credits ###

  * <a href="http://blog.metawrap.com/blog/IEClosuresLeaks.aspx" target="_blank">IEClosuresLeaks</a>
