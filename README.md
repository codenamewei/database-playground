# :card_file_box: SQL Keywords

### BASIC

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **SELECT** | Select rows and colums from table | **SELECT** * FROM tbl |
| **SELECT DISTINCT** | Return only distinct (different) values | **SELECT DISTINCT** name FROM tbl WHERE ID % 2 = 0 |
| **IN**| Specify multiple values in a WHERE clause |  SELECT color FROM table WHERE color **IN** ('red', 'blue') | 
| **NOT IN**| Specify multiple values not in a WHERE clause |  SELECT * FROM customers WHERE first_name NOT IN ('John', 'Jake', 'Julia') | 
| **LENGTH(..)** | Returns the number of characters in a string | SELECT **LENGTH(str)** FROM tbl |
| **ORDER BY .. ASC/DESC** | Arrange sequence according to alphabetically/numbering order | SELECT CITY, LENGTH(CITY) FROM STATION **ORDER BY** LENGTH(CITY), CITY ASC |
| **LIMIT ..** | Limit number of returns | SELECT CITY, LENGTH(CITY) FROM STATION ORDER BY LENGTH(CITY), CITY ASC **LIMIT 1** |


### AGGREGATE

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **SUM(..)** | Total sum of a numeric column | SELECT SUM(id) FROM tbl |
| **AVG(..)** | Average value of a numeric column| To be added |
| **COUNT(..)** | Number of rows that matches a specified criterion | To be added |
| **MIN(..)** | Smallest value of the selected column | To be added |
| **MAX(..)** | Largest value of the selected column | To be added |


### ROUNDING

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **ROUND(..)** | Rounds a number to a specified number of decimal place | To be added |
| **CEIL(..)** | Returns the smallest integer value that is bigger than or equal to a number | To be added |
| **FLOOR(..)** | Returns the largest integer value that is smaller than or equal to a number | To be added |

### NULL (Related)

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **IS NULL** | Check if value is null | SELECT name FROM city WHERE countrycode **IS NULL** |
| **IS NOT NULL** | Check if value is not null | SELECT name FROM city WHERE countrycode **IS NOT NULL** |

### JOIN

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **JOIN** | Check if value is null | SELECT name FROM city WHERE countrycode **IS NULL** |



## Other Notes 

**Database systems that uses SQL**
- Amazon Redshift
- PostgreSQL
- MySQL
- Oracle Database
- Microsoft SQLServer
