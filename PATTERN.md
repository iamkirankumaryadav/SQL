# Pattern Matching

Allows to Search for `Pattern` in Data ( If you don't know the Exact Word or Phrase )

`LIKE` Operator is used in a `WHERE` Clause to Search for a Specified Pattern in a Column.

The Percent Sign ( `%` ) represents Zero, One or Multiple Characters.

The Underscore Sign ( `_` ) represents Single Character.

LIKE Operator |	Description
--- | ---
'a%' |	Finds any values that `start` with "a"
'%a'	| Finds any values that `end` with "a"
'%or%' |	Finds any values that have "or" in `any` position
'\_r%'	| Finds any values that have "r" in the `second` position
'a_%'	| Finds any values that `start` with "a" and are at least 2 characters in length
'a__%' |	Finds any values that `start` with "a" and are at least 3 characters in length
'a%o' | Finds any values that `start` with "a" and `ends` with "o"

```SQL
SELECT Column1, Column2
FROM TableName
WHERE Column1 LIKE 'a%';
```
Symbol | Description |	Example
--- | --- | ---
`*` or `%` |	Represents `Zero` or `More` Characters | bl* finds bl, black, blue, and blob
`?` or `_` |	Represents a `Single` Character |	h?t finds hot, hat, and hit
`[ ]` |	Represents any `Single` Character within the brackets |	h\[oa]t finds hot and hat, but not hit
`!` or `^` |	Represents any character not in the brackets | h\[!oa]t finds hit, but not hot and hat
`-`	| Represents a range of characters | c\[a-b]t finds cat and cbt
`#`	| Represents any single numeric character |	2#5 finds 205, 215, 225, 235, 245, 255, 265, 275, 285, and 295

1. Select Employee Names `Starting` with 'K'
```SQL
SELECT * 
FROM Employee
WHERE Name LIKE 'K%';
```

2. Select Employee Name that have 'Kumar' in `Any` position
```SQL
SELECT * 
FROM Employees
WHERE Name LIKE '%Kumar%';
```

3. Select Employee Name that have 's' in the `Second` Position
```SQL
SELECT * 
FROM Employee
WHERE Name LIKE '_i%';
```

4. Select Employee Name that Starts with 'A' and are atleast `4` Characters in Length

( Amit, Anil, Adil )

```SQL
SELECT * 
FROM Employees
WHERE Name LIKE 'A___%';
```

5. Select Employee Name that Starts with 'S' and End with 'a'

( Smita, Sunita, Sneha, Shweta ... )

```SQL
SELECT * 
FROM Employee
WHERE Name LIKE 's%a';
```

6. Select all EMployee Names that do not starts with 'a'
```SQL
SELECT * 
FROM Employees
WHERE Name NOT LIKE 'a%';
```

7. All Customer Names with First Character is a Letter in the Range A through F
```SQL
SELECT * 
FROM Employee 
WHERE Name LIKE '[A-F]%';
```

8. All Employee Names containing Exactly 5 Characters
```SQL
SELECT * 
FROM Employees
WHERE Name LIKE '_____';
```

9. All Employee Names that Starts with 'Kiran' or 'Yadav'
```SQL
SELECT * 
FROM Employees
WHERE Name LIKE 'Kiran' OR Name LIKE 'Yadav';
```
