### '^' and '$'
These symbols indicate the start and the end of a string, respectively:

| Expression | Description |
| ---------------------  | --------------- |
| **"^The"** | matches any string that starts with "The". | 
| **"of despair$"** | matches a string that ends in with "of despair". | 

### Bracket expressions
Specify which characters are allowed in a single position of a string:

| Expression | Description |
| ---------------------  | --------------- |
| **"[ab]"** | matches a string that has either an a or b (that's the same as **"a\|b"**) | 
| **"[a-d]"** | a string that has lowercase letters 'a' through 'd' (that's equal to **"a\|b\|c\|d"** and even **[abcd]**) | 
| **"[^ab]"** | matches a string that has doesn't start with an a or b | 


### Examples

- Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION.
  - ```SELECT CITY FROM STATION WHERE CITY REGEXP '^[aeiou]'``` 
- Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters.
  - ```SELECT DISTINCT CITY FROM STATION WHERE CITY REGEXP "^[aeiou]" AND CITY REGEXP "[aeiou]$"```
- Query the list of CITY names from STATION that do not start with vowels. 
  - ```SELECT DISTINCT CITY FROM STATION WHERE CITY REGEXP "^[^aeiou]"``` 
### References
- https://dl.icewarp.com/online_help/203030104.htm
