# Queries

Query the List of City Names from A Table that do not Start with `Vowels` and do not End with `Vowels` + Result cannot contain Duplicates.

SUBSTRING(Column, Index, Length)

```SQL
SELECT DISTINCT City 
FROM Employee
WHERE SUBSTRING(City, 1, 1) NOT IN ('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U')
AND SUBSTRING(City, -1, 1) NOT IN ('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U');
```

Query Name of Students who Scored Higher than `75` Marks.

Order by the Last `3` Characters of Each Name.

( If `2` or more Students both have Names ending in the Same Last `3` Characters ( i.e. Kavya, Navya, etc ) Sort them by ID in Ascending Order )

```SQL
SELECT Name 
FROM Students
WHERE Marks > 75
ORDER BY SUBSTRING(Name, -3, 3), ID;
```
