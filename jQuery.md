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

<u>Ajax</u><br>
Ajas is a technique for loading data into part of a page without having to refresh the entire page. The data is often sent in a **JSON** format (JavaScript Object Notation).<br>
When using Ajax:<br>
1. The browser requests info. from the server.
2. The server responds with data (usually HTML, SML, or JSON).
3. The browser processes the content and adds it to the page.

-Asynchronous: Ajax uses an asyncronous processing model. This means the user can do other things while the web browser is waiting for the data to load, speeding up the user experience.
```
//Loading HTML with AJAX

var xhr = new XMLHttpRequest();

xhr.onload = function() {
  if(xhr.status === 200) {
    document.getElementById('content').innerHTML = xhr.responseText;
  }
};
```
```
// Loading JSON with AJAX

var xhr = new XMLHttpRequest();

xhr.onload = function() {
  if(xhr.status === 200) {
    responseObject = JSON.parse(xhr.responseText);

    var newContent = '';
    for (var i = 0; i < responseObject.events.length; i++) {
      newContent += '<div class="event>';
      newContent += 'img src="' + responseObject.events[i].map + '" ';
      newContent += 'alt="' + responseObject.events[i].location + '" />';
      newContent += '<p><b>' + responseObject.events[i].location + ' </b></p>';
      newContent += responseObject.events[i].date + '</p>';
      newContent += '</div>';
    }
    document.getElementbyId('content').innerHTML = newContent;
  }
};
```
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
