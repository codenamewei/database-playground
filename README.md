# :card_file_box: SQL Keywords

### Basic Statements

| Select Statements | Description | Example |
| ---------------------  | --------------- | --------------- |
| **SELECT** | Select all rows and columns from table tbl | **SELECT** * FROM tbl |
| **IN**| Specify multiple values in a WHERE clause |  SELECT color FROM table WHERE color **IN** ('red', 'blue') | 
| Row 3 Column 1 | Row 3 Column 2 |  Row 3 Column 3 | 


### NULL Functions, Statements

| NULL Statements | Description | Example |
| ---------------------  | --------------- | --------------- |
| **IS NULL** | Check if value is null | SELECT name FROM city WHERE countrycode **IS NULL** |
| **IS NOT NULL** | Check if value is not null | SELECT name FROM city WHERE countrycode **IS NOT NULL** |
