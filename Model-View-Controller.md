# Model-View-Controller

Trygve maintains a page that explains the history of MVC in his own words. He arrives at these definitions in a paper he published on December 10th, 1979:

Model = HTML<br>	
View = CSS<br>
Controller = Browser<br>

<u>Models</u><br>
Models represent knowledge. A model could be a single object (rather uninteresting), or it could be some structure of objects.

There should be a one-to-one correspondence between the model and its parts on the one hand, and the represented world as perceived by the owner of the model on the other hand.

<u>Views</u><br>
A view is a (visual) representation of its model. It would ordinarily highlight certain attributes of the model and suppress others. It is thus acting as a presentation filter.

A view is attached to its model (or model part) and gets the data necessary for the presentation from the model by asking questions. It may also update the model by sending appropriate messages. All these questions and messages have to be in the terminology of the model, the view will therefore have to know the semantics of the attributes of the model it represents.

<u>Controllers</u><br>
A controller is the link between a user and the system. It provides the user with input by arranging for relevant views to present themselves in appropriate places on the screen. It provides means for user output by presenting the user with menus or other means of giving commands and data. The controller receives such user output, translates it into the appropriate messages and pass these messages on to one or more of the views.

1. Model
The HTML is the "skeleton" of bedrock content. Text that communicates information to the reader.<br>
OR<br>
The classes which are used to store and manipulate state, typically in a database of some kind.

2. View
The CSS adds visual style to the content. It is the "skin" that we use to flesh out our skeleton and give it a particular look. We can swap in different skins via CSS without altering the original content in any way. They are relatively, but not completely, independent.<br>
OR<br>
The user interface bits (in this case, HTML) necessary to render the model to the user.

3. Controller
The browser is responsible for combining and rendering the CSS and HTML into a set of final, manipulatible pixels on the screen. It gathers input from the user and marshals it to any JavaScript code necessary for the page to function. But here, too, we have flexibility: we can plug in a different brower and get comparable results. Some browsers might render it faster, or with more fidelity, or with more bells and whistles.<br>
OR<br>
The brains of the application. The controller decides what the user's input was, how the model needs to change as a result of that input, and which resulting view should be used.

**Skinnability cuts to the very heart of the MVC pattern.**<br> 
If your app isn't "skinnable", that means you've probably gotten your model's chocolate in your view's peanut butter, quite by accident. You should refactor your code so that only the controller is responsible for poking the model data through the relatively static templates represented by the view.

Here's one quick way to test if your application has properly segregated itself between the Model, View, and Controller roles: is your app **skinnable**?

>My experience is that designers don't understand loops or any kind of state. They do understand templates with holes in them. Everybody understands mail merge. And if you say, "Apply the bold template to this hole," they kind of get that, too. So separating model and view addresses this very important practical problem of how to have designers work with coders.

>The other problem is there is no way to do multiple site skins properly if you don't have proper separation of concerns. If you are doing code generation or sites with different skins on them, there is no way to properly make a new skin by simply copying and pasting the old skin and changing it. If you have the view and the logic together, when you make a copy of the view you copy the logic as well. That breaks one of our primary rules as developers: have only one place to change anything.


