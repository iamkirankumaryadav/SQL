# **Pattern Matching**

- Allows to Search for **Pattern** in the data (If you don't know the exact word)
- **LIKE** Operator is used with a **WHERE** clause to search for a specific pattern in a column.
- The percentage sign **"%"** represents starting or ending reference.
- The underscore sign **"_"** represents single character.

**LIKE Operator** |	**Description**
--- | ---
**'a%'** |	Finds any values that start with "a"
**'%a'**	| Finds any values that end with "a"
**'%or%'** | Finds any values that have "or" in any position
**'_r%'**	| Finds any values that have "r" in the second position
**'a_%'**	| Finds any values that start with "a" and are at least 2 characters in length
**'a__%'** |	Finds any values that start with "a" and are at least 3 characters in length
**'a%o'** | Finds any values that start with "a" and end with "o"

```SQL
SELECT column1, column2
FROM table_name
WHERE column1 LIKE 'a%';
```
Symbol | Description |	Example
--- | --- | ---
'*' or '%' |	Represents zero or more characters | bl* finds bl, black, blue, and blob
? or _ |	Represents a single character |	h?t finds hot, hat, and hit
'[ ]' |	Represents any single character within the brackets |	h[oa]t finds hot and hat, but not hit
'!' or ^ |	Represents any character not in the brackets | h[!oa]t finds hit, but not hot and hat
'-'	| Represents a range of characters | c[a-b]t finds cat and cbt
'#'	| Represents any single numeric character |	2#5 finds 205, 215, 225, 235, 245, 255, 265, 275, 285, and 295

1. Select employee names starting with 'K'
```SQL
SELECT * 
FROM employee
WHERE name LIKE 'K%';
```

2. Select employee name that have 'Kumar' at any position
```SQL
SELECT * 
FROM employees
WHERE name LIKE '%Kumar%';
```

3. Select employee name that have 's' at the second position
```SQL
SELECT * 
FROM employee
WHERE name LIKE '_i%';
```

4. Select employee name that starts with 'A' and are atleast 4 characters in length e.g. Amit, Anil, Adil

```SQL
SELECT * 
FROM employees
WHERE name LIKE 'A___%';
```

5. Select employee name that start with 'S' and end with 'a' e.g. Smita, Sunita, Sneha, Shweta 

```SQL
SELECT * 
FROM employee
WHERE name LIKE 's%a';
```

6. Select all employee names that do not starts with 'a'
```SQL
SELECT * 
FROM employees
WHERE name NOT LIKE 'a%';
```

7. All customer names with first character is a letter in the range A through F
```SQL
SELECT * 
FROM employee 
WHERE name LIKE '[A-F]%';
```

8. All employee names containing exactly 5 characters
```SQL
SELECT * 
FROM employees
WHERE name LIKE '_____';
```

9. All employee names that start with 'Kiran' or 'Yadav'
```SQL
SELECT * 
FROM employees
WHERE name LIKE 'Kiran' OR name LIKE 'Yadav';
```
