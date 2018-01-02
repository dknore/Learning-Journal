# Databases


----------------------------------
## Setting up a Database

### <u>Terminal</u>:
1.	mkdir todos (touch server.js .gitignore)     // Name of Table + add files
2.	mkdir public (touch index.html app.js
3.	git init     // initialize
4.	create dateabase todos;
5.	\c  todos    // cd into database
--------------------------------
6.	create table todolist(
id serial primary key,
task varchar(255) NOT NULL,
completed DATE);
7.	\d todolist
8.	INSERT INTO todolist
9.	(task) values('buy milk');
10.	select * from todolist;
----------------------------------
11.	npm init -y   // initialize database
12.	npm install express body-parser pg

### <u>server.js</u>:
1.	Require DEPENDENCIES:
o	const pg = require('pg');
o	const express = require('express');
o	const bodyParser = require('body-parser');

2.	Define CONSTANTS:
o	const PORT = process.env.PORT || 3000;
o	const app = express();
o	const conString = 'postgres://localhost:5432;    // User Password
o	const client = new pg.Client('postgres://localhost:5432/some_db');

3.	Add LISTENER
o	app.listen(PORT, function () {
      console.log('server started on: ' + PORT);
     });

4.	CONNECT to our Database:
o	client.connect();

5.	INSTALL middleware plug-ins:
o	app.use(bodyParser.json());
o	app.use(bodyParser.urlencoded({extended: true}));
o	app.use(express.static('./public'));

6.	Routes for REQUESTING HTML recourses:
o	app.get('/new', (request, response) => {
      response.sendFIle('new.html', {root: './public'});
      });
o	app.get('/articles', (request, response) => {
      client.query('SELECT * FROM articles')
        .then(function(result) {
           response.send(result.rows);
      })
        .catch(function(err) {
           console.error(err)
      })
});
o	app.post('/articles', (request, response) => {
      client.query(
	'INSERT INTO
	articles(title, author, "authorURL", category)
      });
o	

## JOINING Multiple Tables

1) S
elect desired columns OR ALL from table of origin 
```
SELECT * FROM table1
```
2) Join with desired table
```
INNER JOIN table2
```
3) Identify columns from table1 to be joined to columns from table2
```
ON articles.author_Id = authors.author_id
```
4) Optional filters:
```
ORDER BY publishedOn DESC
```

## Data Structure

### Storing Data:  

<u>Arrays</u>

Storing Objects in an ARRAY:<br>
When the order of the objects is important, they should be stored in an array because each item in an array is given an index number.
```
var people = [
      {name: 'Casey', age: 10},
      {name: 'Camille', age: 13}
]
```
<u>Properties</u><br>
Storing Objects as PROPERTIES:<br>
When you want to access objects using their name, they work well as properties of another object (because you wouldn't need to iterate through all of the objecst as you would in an array).
```
var people = {
      Casey: {age: 10}, 
      Camille: {age: 13}
}
```
<u>Storing References to Objects & DOM Nodes</u><br>
- ROW arrays:

- PEOPLE arrays:

<br>

### Filtering Data
- Dynamic Filtering:
- Filtering an Array:
