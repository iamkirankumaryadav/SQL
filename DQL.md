# `DQL` : Data Query Language

Keyword Comparison Operators 
```
1. BETWEEN     : Returns data within range of values.
2. IN          : Returns data within a list of values.
3. LIKE        : Returns data similar to given pattern (Using Wildcard)
4. IS NULL     : Returns null values.
5. IS NOT NULL : Returns not null values.
6. EXISTS      : Determine if a subquery returns values or not.
```
Querying the table with logical operator `LIKE` :
```sql
Underscore : _

SELECT Code from Table
WHERE Code LIKE '_2_6'

Results :
'1216'
'1226'
'1236'...
```

```sql
Square Brackets : [ ] | or

SELECT Last_Name 
FROM Employee
WHERE Last_Name LIKE 'Wi[lk]%' # 'Wi' followed with either 'l' or 'k'

Results :
'Williams'
'Wiki'
'Wikipedia'
```

```sql
Percentage : %  

------------------------------
Get only Google mails :

SELECT First_Name, Email 
FROM Employee
WHERE Email LIKE '%@gmail.com'

------------------------------
Get mails another than gmail

SELECT First_Name, Email
FROM Employee
WHERE Email NOT LIKE '%@gmail.com' 

----------------------------------

SELECT First_Name, City
FROM Employee
WHERE First_Name LIKE 'B[iro]%' AND City NOT LIKE '%UL%'
```

