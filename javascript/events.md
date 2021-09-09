
# Events


## onload(), onContentChecked() & $(document).ready()
onContentChecked() event occurs after the HTML document has been loaded 
(i.e. DOM hierarchy has been fully constructed). 

The DOMContentLoaded event is fired when the document has been completely loaded and parsed, 
without waiting for stylesheets, images, and subframes.  
The onload() event occurs when the documetn and all its resources all loaded.  

$(document).ready() event is jQuery equivalent to DOMContentLoaded

```
$(document).ready(function() {
   console.log( "ready!" );
});
```