# SQL Keywords [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

### BASIC

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **SELECT** | Select rows and colums from table | **SELECT** * FROM tbl |
| **SELECT DISTINCT** | Return only distinct (different) values | **SELECT DISTINCT**(front_name), last_name from tbl |
| **IN**| Specify multiple values in a WHERE clause |  SELECT color FROM table WHERE color **IN** ('red', 'blue') | 
| **NOT IN**| Specify multiple values not in a WHERE clause |  SELECT * FROM customers WHERE first_name NOT IN ('John', 'Jake', 'Julia') | 
| **LENGTH(..)** | Returns the number of characters in a string | SELECT **LENGTH(str)** FROM tbl |
| **ORDER BY .. ASC/DESC** | Arrange sequence according to alphabetically/numbering order | SELECT CITY, LENGTH(CITY) FROM STATION **ORDER BY** LENGTH(CITY), CITY ASC |
| **LIMIT** | Limit number of returns | SELECT CITY, LENGTH(CITY) FROM STATION ORDER BY LENGTH(CITY), CITY ASC **LIMIT 1** |
| **AS** | Alias for display. Only been used in the data output. Cannot used for filtering | SELECT COUNT(amount) **AS** num_transactions FROM payment |
| **GROUP BY** | Group rows that have the same values | SELECT COUNT(CustomerID), Country FROM Customers **GROUP BY **Country; |
| **CAST** | Converts a value (of any type) into a specified datatype | SELECT **CAST**(ID AS FLOAT) FROM Students WHERE Name = 'Samantha' |
| **HAVING** | Filter after aggregation have take place |  SELECT SUM(SALES) FROM tbl **HAVING** SUM(SALES) > 1000 |
| **CONCAT(..)** | Adds two or more strings together | **CONCAT**('+', country_code, phone_number) |

### INTERMEDIATE
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
CASE
WHEN A = B THEN "It's a match"
ELSE "Nothing match"
END
FROM TRIANGLES;
```


### AGGREGATE

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **SUM(..)** | Total sum of a numeric column | SELECT SUM(id) FROM tbl |
| **AVG(..)** | Average value of a numeric column| To be added |
| **COUNT(..)** | Number of rows that matches a specified criterion | To be added |
| **MIN(..)** | Smallest value of the selected column | To be added |
| **MAX(..)** | Largest value of the selected column | To be added |


### Mathematics

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **ROUND(..)** | Rounds a number to a specified number of decimal place | SELECT ROUND(salary, 2) FROM tbl WHERE name = 'john doe' |
| **CEIL(..)** | Returns the smallest integer value that is bigger than or equal to a number | To be added |
| **FLOOR(..)** | Returns the largest integer value that is smaller than or equal to a number | To be added |
| **ABS(..)** | Returns absolute values | SELECT **ABS**(MAX(value) - MIN(value)) FROM tbl|


### NULL (Related)

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **IS NULL** | Check if value is null | SELECT name FROM city WHERE countrycode **IS NULL** |
| **IS NOT NULL** | Check if value is not null | SELECT name FROM city WHERE countrycode **IS NOT NULL** |

### JOIN & UNION

| Functions | Description | Example |
| ---------------------  | --------------- | --------------- |
| **(INNER) JOIN** | Selects records that have matching values in both table | SELECT Students.ID, Name, Friend_ID FROM Students JOIN Friends ON Students.ID = Friends.ID |
| **FULL OUTER JOIN** | Selects all records | SELECT * FROM Registrations FULL OUTER JOIN Logins ON Registrations.name = Logins.name |
| **UNION** | Join results together | SELECT * from tbl **UNION** SELECT * from tbl2 ORDER BY name |

_Note_:
[JOIN Reference](https://blog.codinghorror.com/a-visual-explanation-of-sql-joins/)



