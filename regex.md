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
| **"[ab]"** | matches a string that has either an a or a b (that's the same as **"a\|b"**) | 
| **"[a-d]"** | a string that has lowercase letters 'a' through 'd' (that's equal to **"a\|b\|c\|d"** and even **[abcd]**) | 


### References
- https://dl.icewarp.com/online_help/203030104.htm
