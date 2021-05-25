# Queries

Query the List of City Names from A Table that do not Start with `Vowels` and do not End with `Vowels` + Result cannot contain Duplicates.

SUBSTRING(Column, Index, Length)

```SQL
SELECT DISTINCT City 
FROM Employee
WHERE SUBSTRING(City, 1, 1) NOT IN ('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U')
AND SUBSTRING(City, -1, 1) NOT IN ('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U')
```
