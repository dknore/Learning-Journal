# SQL

**Structured Query Language (SQL)**, is a language designed to allow both technical and non-technical users to query, manipulate, and transform data from a relational database. And due to its simplicity, SQL databases provide safe and scalable storage for millions of websites and mobile applications.

### Relational databases

A relational database represents a collection of related (two-dimensional) tables. Each of the tables are similar to an Excel spreadsheet, with a fixed number of named columns (the attributes or properties of the table) and any number of rows of data.

For example, if the Department of Motor Vehicles had a database, you might find a table containing all the known vehicles that people in the state are driving. This table might need to store the model name, type, number of wheels, and number of doors of each vehicle for example.
```
Table: Vehicles
Id	Make/Model	# Wheels	# Doors	Type
1	Ford Focus	4	4	Sedan
2	Tesla Roadster	4	2	Sports
3	Kawakasi Ninja	2	0	Motorcycle
4	McLaren Formula 1	4	0	Race
5	Tesla S	4	4	Sedan
```
In such a database, you might find additional related tables containing information such as a list of all registered drivers in the state, the types of driving licenses that can be granted, or even driving violations for each driver.

By learning SQL, the goal is to learn how to answer specific questions about this data, like "What types of vehicles are on the road have less than four wheels?", or "How many models of cars does Tesla produce?", to help us make better decisions down the road.

### LESSON 1: SELECT queries

To retrieve data from a SQL database, we need to write SELECT statements, which are often colloquially refered to as queries. A query in itself is just a statement which declares what data we are looking for, where to find it in the database, and optionally, how to transform it before it is returned.
```
// Select query for a specific columns
SELECT column, another_column, …
FROM mytable;

//Select query for all columns
SELECT * 
FROM mytable;
```
### LESSON 2: Queries with constraints (Pt. 1)

In order to filter certain results from being returned, we need to use a **WHERE** clause in the query. The clause is applied to each row of data by checking specific column values to determine whether it should be included in the results or not.
```
// Select query with constraints
SELECT column, another_column, …
FROM mytable
WHERE condition
    AND/OR another_condition
    AND/OR …;
```
```

Operator	Condition	SQL Example
=, !=, < <=, >, >=	Standard numerical operators	col_name != 4
BETWEEN … AND …	Number is within range of two values (inclusive)	col_name BETWEEN 1.5 AND 10.5
NOT BETWEEN … AND …	Number is not within range of two values (inclusive)	col_name NOT BETWEEN 1 AND 10
IN (…)	Number exists in a list	col_name IN (2, 4, 6)
NOT IN (…)	Number does not exist in a list	col_name NOT IN (1, 3, 5)
```
NOTE:
As you might have noticed by now, SQL doesn't require you to write the keywords all capitalized, but as a convention, it helps people distinguish SQL keywords from column and tables names, and makes the query easier to read.

### LESSON 3: Queries with constraints (Pt. 2)

When writing WHERE clauses with columns containing text data, SQL supports a number of useful operators to do things like case-insensitive string comparison and wildcard pattern matching. We show a few common text-data specific operators below:
```

Operator	Condition	Example
=	Case sensitive exact string comparison (notice the single equals)	col_name = "abc"
!= or <>	Case sensitive exact string inequality comparison	col_name != "abcd"
LIKE	Case insensitive exact string comparison	col_name LIKE "ABC"
NOT LIKE	Case insensitive exact string inequality comparison	col_name NOT LIKE "ABCD"
%	Used anywhere in a string to match a sequence of zero or more characters (only with LIKE or NOT LIKE)	col_name LIKE "%AT%"
(matches "AT", "ATTIC", "CAT" or even "BATS")
_	Used anywhere in a string to match a single character (only with LIKE or NOT LIKE)	col_name LIKE "AN_"
(matches "AND", but not "AN")
IN (…)	String exists in a list	col_name IN ("A", "B", "C")
NOT IN (…)	String does not exist in a list	col_name NOT IN ("D", "E", "F")
```
### 4. Filtering and sorting Query results

Even though the data in a database may be unique, the results of any particular query may not be – take our Movies table for example, many different movies can be released the same year. In such cases, SQL provides a convenient way to discard rows that have a duplicate column value by using the **DISTINCT** keyword.
```
// Select query with unique results
SELECT DISTINCT column, another_column, …
FROM mytable
WHERE condition(s);
```
Since the **DISTINCT** keyword will blindly remove duplicate rows, we will learn in a future lesson how to discard duplicates based on specific columns using grouping and the **GROUP BY** clause.
#### Ordering results
Unlike our neatly ordered table in the last few lessons, most data in real databases are added in no particular column order. As a result, it can be difficult to read through and understand the results of a query as the size of a table increases to thousands or even millions rows.

To help with this, SQL provides a way to sort your results by a given column in ascending or descending order using the **ORDER BY** clause.
```
// Select query with ordered results
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC;
```
When an **ORDER BY** clause is specified, each row is sorted alpha-numerically based on the specified column's value. In some databases, you can also specify a collation to better sort data containing international text.
####  Limiting results to a subset
Another clause which is commonly used with the **ORDER BY** clause are the **LIMIT** and **OFFSET** clauses, which are a useful optimization to indicate to the database the subset of the results you care about.
The **LIMIT** will reduce the number of rows to return, and the optional **OFFSET** will specify where to begin counting the number rows from.
```
// Select query with limited rows
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```
NOTE:
 The LIMIT and OFFSET are applied relative to the other parts of a query, they are generally done last after the other clauses have been applied.

### LESSON 13: Inserting rows

#### Schema
In SQL, the **database schema** is what describes the structure of each table, and the datatypes that each column of the table can contain.

For example:
In our Movies table, the values in the Year column must be an Integer, and the values in the Title column must be a String.

#### Inserting new data
```
// Insert statement with values for all columns
INSERT INTO mytable
VALUES (value_or_expr, another_value_or_expr, …),
       (value_or_expr_2, another_value_or_expr_2, …),
```
```
// Insert statement with specific columns
INSERT INTO mytable
(column, another_column, …)
VALUES (value_or_expr, another_value_or_expr, …),
      (value_or_expr_2, another_value_or_expr_2, …),
      …;
```
In these cases, the number of values need to match the number of columns specified. Despite this being a more verbose statement to write, inserting values this way has the benefit of being forward compatible. For example, if you add a new column to the table with a default value, no hardcoded  **INSERT** statements will have to change as a result to accommodate that change.

In addition, you can use mathematical and string expressions with the values that you are inserting.
This can be useful to ensure that all data inserted is formatted a certain way.
```
// Example Insert statement with expressions
INSERT INTO boxoffice
(movie_id, rating, sales_in_millions)
VALUES (1, 9.9, 283742034 / 1000000);
```
### Lesson 14: Updating rows
In addition to adding new data, a common task is to update existing data, which can be done using an **UPDATE** statement. Similar to the **INSERT** statement, you have to specify exactly which table, columns, and rows to update. In addition, the data you are updating has to match the data type of the columns in the table schema.

