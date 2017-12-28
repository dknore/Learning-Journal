# Ajax<br>
Ajax is a technique for loading data into part of a page without having to refresh the entire page. The data is often sent in a **JSON** format (JavaScript Object Notation).<br>
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