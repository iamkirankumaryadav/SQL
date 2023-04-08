# `DQL` : Data Query Language

`Fetch` the data from the database.

`SELECT` the attribute based on the conditions described by `WHERE` clause.

Keyword Comparison Operators 
```
1. BETWEEN     : Returns data within range of values.
2. IN          : Returns data within a list of values.
3. LIKE        : Returns data similar to given pattern (Using Wildcard)
4. IS NULL     : Returns null values.
5. IS NOT NULL : Returns not null values.
6. EXISTS      : Determine if a subquery returns values or not.
```
### Querying the table with logical operator `LIKE` :
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

### Querying ythe table with logical operators IN and BETWEEN

```sql
SELECT First_Name, Shirt_Size 
FROM Customer
WHERE Shirt_Size IN ('M', 'L', 'XL', 'XXL')
ORDER BY Shirt_Size ASC
```

```sql
SELECT First_Name, Pant_Size, DATENAME(Month, Birthday) as BirthMonth 
FROM Customer
WHERE Dress_Size BETWEEN 2 AND 16 AND Pant_Size LIKE '%L'
ORDER BY BirthMonth
```

```sql
SELECT First_Name, DATENAME(Year, Birthday) as BirthYear 
FROM Customer
WHERE Birthday BETWEEN '1980' AND '1982'
ORDER BY BirthYear DESC
```

### `COALESCE`
Return the first non null value in the list.
```sql
SELECT First_Name, Last_Name, Starting_Salary, Current_Salary, 
COALESCE(Current_Salary*1.1, Starting_Salary) AS New_Salary 
FROM Employee
WHERE Starting_Salary <= 35000
```
