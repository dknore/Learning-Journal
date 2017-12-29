# Databases

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
