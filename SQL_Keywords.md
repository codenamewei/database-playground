# SQL Keywords 

SQL Syntax that can be applied to any major type of SQL Database (MySQL, Oracle, PostGreSQL...)

Table of Contents
-----------------

- [Basic](#basic)
    - [Select](#select)
    - [Aggregate](#aggregate)
    - [Range](#range)
    - [Mathematics](#mathematics)
    - [Constraint](#constraint)
    - [Others](#others-basic)
- [Intermediate](#intermediate)
    - [Create](#create)
    - [Like](#like)
    - [String Operation](#string-operation)
    - [Others](#others-intermediate)
- [Advanced](#advanced)
    - [CASE](#case)
    - [JOIN](#join)
    - [VARIABLE](#variable)
    - [VIEW](#view)
    - [Others](#others-advanced)
- [Other Notes](#other-notes)

## BASIC

### SELECT
| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **SELECT** | Select rows and colums from table | **SELECT** * FROM tbl;<br />**SELECT** * FROM tbl as tb; |
| **SELECT DISTINCT** | Return only distinct (different) values | **SELECT DISTINCT**(front_name), last_name from tbl |
| **SELECT IF**<br /> - [ ] Postgresql<br /> - [x] Mysql| Return "YES" if the condition is TRUE, or "NO" if the condition is FALSE | **SELECT IF**(GRADE < 8, NULL, NAME) ...|


### AGGREGATE

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **SUM(..)** | Total sum of a numeric column | SELECT SUM(id) FROM tbl |
| **AVG(..)** | Average value of a numeric column| To be added |
| **COUNT(..)** | Number of rows that matches a specified criterion | SELECT COUNT(DISTINCT employee_id) FROM student; |
| **MIN(..)** | Smallest value of the selected column | To be added |
| **MAX(..)** | Largest value of the selected column | To be added |
| **GROUP BY** | Group rows that have the same values | SELECT COUNT(CustomerID), Country FROM Customers **GROUP BY** Country, Country_id;|
| **HAVING** | Filter after aggregation have take place |  SELECT SUM(SALES) FROM tbl **HAVING** SUM(SALES) > 1000 |

__Note:__
- Aggregate function happens only in the SELECT clause or the HAVING clause
- While COUNT(*) is possible, it's good to provide COUNT(ITEM) to provide clarity


### RANGE

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **IN** | Specify multiple values in a WHERE clause |  SELECT color FROM table WHERE color **IN** ('red', 'blue') | 
| **NOT IN** | Specify multiple values not in a WHERE clause |  SELECT * FROM customers WHERE first_name NOT IN ('John', 'Jake', 'Julia') | 
| **BETWEEN** | Selects values within a given range.<br />**Operator is inclusive: begin and end values are included** |  SELECT * FROM student WHERE percentage between 20 AND 60<br />Same as:<br />SELECT * FROM student WHERE percentage > 20 AND percentage < 60; | 
| **NOT BETWEEN** | Select values not within a given range. | SELECT * FROM products WHERE price NOT BETWEEN 10 AND 20; |


```
#Combination of RANGE keywords ( Between and In)

SELECT * FROM products
WHERE price BETWEEN 10 AND 20
AND category_id NOT IN (1,2,3);
```

### MATHEMATICS

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **ROUND(..)** | Rounds a number to a specified number of decimal place | SELECT ROUND(salary, 2) FROM tbl WHERE name = 'john doe' |
| **CEIL(..)** | Returns the smallest integer value that is bigger than or equal to a number | To be added |
| **FLOOR(..)** | Returns the largest integer value that is smaller than or equal to a number | To be added |
| **ABS(..)** | Returns absolute values | SELECT **ABS**(MAX(value) - MIN(value)) FROM tbl|
| **MOD(x, y)** | Returns the remainder of a number divided by another number | SELECT CASE WHEN MOD(4, 2) = 0 THEN 'even number' ELSE 'not an even number' END; |



### Constraint

| Constraint | Description | Example |
| ---------------------  | --------------- | --------------- |
| **NOT NULL** | Enforces a column to NOT accept NULL values | CREATE TABLE mouse<br />(<br />    name VARCHAR(50) **NOT NULL**,<br />    percentage INT **NOT NULL**,<br />    PRIMARY KEY(name)<br />);  |
| **UNIQUE** | Ensures that all values in a column are different.<br />A PRIMARY KEY constraint automatically has a UNIQUE constraint. | CREATE TABLE shop<br />(<br />    coffee VARCHAR(50) NOT NULL,<br />    code INT NOT NULL **UNIQUE**,<br />    PRIMARY KEY(coffee)<br />);  |


### OTHERS-BASIC
| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **IS NULL** | Check if value is null | SELECT name FROM city WHERE countrycode **IS NULL** |
| **IS NOT NULL** | Check if value is not null | SELECT name FROM city WHERE countrycode **IS NOT NULL** |
| **LENGTH(..)** | Returns the number of characters in a string | SELECT **LENGTH(str)** FROM tbl |
| **ORDER BY .. ASC/DESC** | Arrange sequence according to alphabetically / numbering order. <br />It's a good practice to explicitly mention ASC, DESC to provide clarity in the future | SELECT CITY, LENGTH(CITY) FROM STATION **ORDER BY** LENGTH(CITY), CITY ASC;<br />SELECT * FROM student<br />**ORDER BY** percentage DESC LIMIT 2;|
| **LIMIT** | Limit number of returns | SELECT CITY, LENGTH(CITY) FROM STATION ORDER BY LENGTH(CITY), CITY ASC **LIMIT 1** |
| **AS** | Alias for display. Only been used in the data output. Cannot used for filtering | SELECT COUNT(amount) **AS** num_transactions FROM payment |
| **CAST** | Converts a value (of any type) into a specified datatype | SELECT **CAST**(ID AS FLOAT) FROM Students WHERE Name = 'Samantha' |
| **WHERE**| Filter records | SELECT * FROM tbl **WHERE** num=123 | 

## INTERMEDIATE

### CREATE

| Functions | Description |
| ---------------------  | --------------- |
| **CREATE TABLE** | Create a new table in the database |
```
#Template

CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);

#Example
CREATE TABLE mytable
(
  id int NOT NULL, 
  username VARCHAR(100) NOT NULL, 
  password VARCHAR(100) NOT NULL, 
  PRIMARY KEY(id)
);
```

| Functions | Description |
| ---------------------  | --------------- |
| **CREATE SCHEMA** | Enters a new schema into the current database |

| Functions | Description |
| ---------------------  | --------------- |
| **INSERT INTO ... VALUES** | Insert values into table | 


```
#Template
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

#Example
INSERT INTO mytable(id, username, johndoe) 
VALUES (123, 'johndoe', 'door');

#Multiple values input
INSERT INTO mytable 
VALUES 
(123, 'johndoe', 'door'),
(456, 'sql csv', 'sql');

```

### LIKE
| Functions | Description |
| ---------------------  | --------------- |
| **LIKE** | WHERE<>LIKE | Search for a specified pattern in a column |
| **NOT LIKE** | WHERE<>NOT LIKE | Search for a specified pattern not in a column |

- LIKE is case sensitve, use ILIKE to be case insensitive
- There are two wildcards often used in conjunction with the LIKE operator:
    - The percent sign (%) represents zero, one, or multiple characters
    - The underscore sign (_) represents one, single character

```
#Template 
SELECT * FROM tbl WHERE name LIKE ???

# The percent sign (%) represents zero, one, or multiple characters
# The underscore sign (_) represents one, single character

       LIKE Operator	                       Description
WHERE CustomerName LIKE 'a%'	Finds any values that start with "a"
WHERE CustomerName LIKE '%a'	Finds any values that end with "a"
WHERE CustomerName LIKE '%or%'	Finds any values that have "or" in any position
WHERE CustomerName LIKE '_r%'	Finds any values that have "r" in the second position
WHERE CustomerName LIKE 'a_%'	Finds any values that start with "a" and are at least 2 characters in length
WHERE CustomerName LIKE 'a__%'	Finds any values that start with "a" and are at least 3 characters in length
WHERE ContactName LIKE 'a%o'	Finds any values that start with "a" and ends with "o"

#Example
SELECT * FROM mytable 
WHERE username LIKE '%doe%'


SELECT * FROM mytable
WHERE username NOT LIKE '%doe%';
```
### STRING OPERATION
| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **LOWER(..)** | Converts a string to lower-case | **LOWER**('String is SAMPLE') |
| **UPPER(..)** | Converts a string to upper-case | **UPPER**('String is SAMPLE') |
| **CONCAT(..)** | Adds two or more strings together | **CONCAT**('+', country_code, phone_number) |
| **SUBSTRING(..)** | Extracts some characters from a string.<br />**Index of string starts from 1, not 0** | Syntax: **SUBSTRING**(string, start, length)<br />**SUBSTRING**(name, 1, 1) |

### OTHERS-INTERMEDIATE

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **DROP TABLE** | Delete table of a specific name | **DROP TABLE** * DROP TABLE mytable |
| **UPDATE .. SET ...WHERE** | Modify records in the table | **UPDATE** mytable **SET** username='john doe' **WHERE** id=0 |
| **DELETE FROM .. WHERE** | Delete records in the table | **DELETE FROM** mytable **WHERE** id=0 |



## Advanced 

### CASE

| Functions | Description |
| ---------------------  | --------------- |
| **CASE(..)** | IF-ELSE STATEMENT |
```
#Template
SELECT CASE
WHEN case THEN result 1
WHEN case THEN result 2
ELSE result
END;

#Example
SELECT
CASE WHEN A = B THEN "It's a match"
ELSE "Nothing match"
END
FROM TRIANGLES;

SELECT name, percentage,
(CASE WHEN percentage < 50 THEN 'Fail' ELSE 'Pass' END) AS remark
FROM student;

SELECT CASE
WHEN percentage <= 35 THEN 'fail'
WHEN percentage > 35 AND percentage < 50 THEN 'pass'
ELSE 'excellent' END AS result,
COUNT(*) AS passing_count
FROM STUDENT
GROUP BY result
```

### JOIN

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **(INNER) JOIN** | Selects records that have matching values in both table | SELECT Students.ID, Name, Friend_ID FROM Students JOIN Friends ON Students.ID = Friends.ID |
| **FULL (OUTER) JOIN** | Selects all records | SELECT * FROM Registrations FULL JOIN Logins ON Registrations.name = Logins.name WHERE Registrations.reg_id IS NULL OR Logins.log_id IS NULL |
| **LEFT (OUTER) JOIN** | Results in the set of records that are in the left table, if there are no match with the right table, the results are null. | SELECT * FROM Registrations LEFT JOIN Logins ON Registrations.name = Logins.name WHERE Logins.login_id IS null |
| **RIGHT (OUTER) JOIN** | Same as LEFT (OUTER) JOIN, except the tables are switched. | SELECT * FROM Registrations RIGHT JOIN Logins ON Registrations.name = Logins.name WHERE Logins.login_id IS null |
| **UNION** | Join results together | SELECT * from tbl **UNION** SELECT * from tbl2 ORDER BY name |

_Note_:
- [JOIN Reference](https://blog.codinghorror.com/a-visual-explanation-of-sql-joins/)
- Implicit JOIN = INNER JOIN
- Order of tables doesnt matter with INNER JOIN

### VARIABLE

MySQL has a concept of user-defined variables.

They are loosely typed variables that may be initialized somewhere in a session and keep their value until the session ends.

They are prepended with an @ sign, like this: @var

Initialize user-define variable with a SET statement:
```
SET @var = 1
```
or inside a query

```
SELECT @var2 := 2
```


### VIEW
Understanding the schema and what tables are in it help to write efficient SQL and helps avoid running queries multiple times just to see if the schema name or column name is correct. 
 
Information Schema provides access to database metadata, information about the MySQL server such as the name of a database or table, the data type of a column, or access privileges.

| View | Description | Example |
| ---------------------  | --------------- | --------------- |
| **INFORMATION_SCHEMA.TABLES** | Provide all tables in the database | SELECT * FROM INFORMATION_SCHEMA.TABLE; |
| **INFORMATION_SCHEMA.COLUMNS** | Provide all columns and tables in the database | SELECT * FROM INFORMATION_SCHEMA.COLUMNS WHERE table_schema = 'public' and table_name = 'signup'; |

### OTHERS-ADVANCED
| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **REPEAT** | Repeat a string for as many times as specified| SET @number = 21;<br /><br />SELECT **REPEAT**('* ', @number := @number - 1) FROM INFORMATION_SCHEMA.TABLES;<br /><br />SELECT REPEAT('* ', @var := @var + 1) FROM INFORMATION_SCHEMA.TABLES WHERE @var < 20; |

## Other Notes
- Avoid using column or table names containing spaces or using reserved words in SQL.  
  For example, avoid names like _table_ or _first name_.
  
- Backticks are mainly used to prevent an error called "MySQL reserved word".  
  Please see the MySQL Manual page entitled [Keywords and Reserved Words](https://dev.mysql.com/doc/refman/8.0/en/keywords.html).  
  The ones with an (R) are Reserved Words. The others are merely Keywords.  
  The Reserved require special caution.
  ```
  SELECT student_name, AVG(test_score) FROM student GROUP BY `group`
  ````
- Other Keywords

| Keywords | Description |
| ---------------------  | --------------- |
| **Database Schema** | [Blueprint/Architecture of Data](https://www.educative.io/blog/what-are-database-schemas-examples) of how the data should looks like.<br />An entry in the database will be an instance of the database schema.   |
| **Data Modelling** | Process of planning a database design |
| **Relational Database Management System** | Software that stores and retrieves user data in a secure way that follows the [ACID](https://blog.sqlauthority.com/2007/12/09/sql-server-acid-atomicity-consistency-isolation-durability/) concept.<br/>Note: Some popular DBMS systems are MySQL, Oracle, PostgreSQL, Microsoft Access, MariaBB, and dBASE, amongst others.|
| **Database Administrator (DBA)** | Individual responsible for database design and DBMS responsibilities including ensuring that data analysts and database users can easily access information. |
| **Logical Database Schema** | Represents how the data is organized in terms of tables |
| **Physical Database Schema** | Represents how data is stored on disk storage. In other words, it is the actual code that will be used to create the structure of the database |
| **Entity-Relationship Modeling** | Create logical database schema to illustrate relationships between data components. |
| **Primary Key** | Identify a record in the table |
| **Foreign Key** | Primay key for another table |
| **Three Schema Architecture** | TBA |
| **Relation Model Concepts** | TBA |
| **Functional Dependencies** | TBA|
| **Normalization** | TBA |

- For more references
    - [SQL Cheat Sheet](https://drive.google.com/file/d/1Pj1FGqJLVadW48195ngmvHPHzekZS0Rf/view?usp=sharing)  


