# jQuery

<u>Events</u><br>
```$('li').on('click', function() {
  $(this).addClass('complete');<br>
});
```
- UI: focus, blur, change
- KEBOARD: input, keydown, keyup, keypress
- MOUSE: click, dblclick, mouseup, mousedown, mouseover, mousemove, mouseout, hover
- FORM: submit, select, change
- DOCUMENT: ready, load, unload
- BROWSER: error, resize, scroll


```
//jQuery's AJAX shorthand
$.get(url[, data][, callback][, type])
$.post(url[, data][, callback][, type])
$.getJSON(url[, data][, callback])
$.getScript(url[, data][, callback])
```

<u>JSON (JavaScript Object Notation)</u><br>
'Objects' cannot be transferred over the network. Instead, data can be formatted using JSON. The page must include:
1. A function that will process the JSON data that the server sends. 
2. A \<script> element whose src attribute will request the JSON data from the remote server.
