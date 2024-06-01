# **Data Query Language (DQL)**

- Fetch the data from the database.
- SELECT the attribute based on the conditions described by the WHERE clause.

Operators | Description
--- | ---
BETWEEN | Returns data within a range of values.
IN | Returns data within a list of values.
LIKE | Returns data similar to the given pattern (Using Wildcard)
IS NULL | Returns null values.
IS NOT NULL | Returns not null values.
EXISTS | Determine if a subquery returns values or not.

### Querying the table with the logical operator `LIKE` :
```sql
# Underscore: _

SELECT Code
FROM Table
WHERE Code LIKE '_2_6'

Results :
'1216'
'1226'
'1236'...
```

```sql
# Square Brackets: [ ] | or

SELECT Last_Name 
FROM Employee
WHERE Last_Name LIKE 'Wi[lk]%' # 'Wi' followed with either 'l' or 'k'

Results :
'Williams'
'Wiki'
'Wikipedia'
```

```sql
# Percentage: %  
------------------------------
# Get only Google mails:

SELECT First_Name, Email 
FROM Employee
WHERE Email LIKE '%@gmail.com'

------------------------------
# Get emails other than Gmail

SELECT First_Name, Email
FROM Employee
WHERE Email NOT LIKE '%@gmail.com' 

----------------------------------

SELECT First_Name, City
FROM Employee
WHERE First_Name LIKE 'B[iro]%' AND City NOT LIKE '%UL%'
```

### Querying the table with logical operators IN and BETWEEN

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

### **COALESCE**

```sql
# Return the first non-null value in the list:
SELECT First_Name, Last_Name, Starting_Salary, Current_Salary, 
COALESCE(Current_Salary*1.1, Starting_Salary) AS New_Salary 
FROM Employee
WHERE Starting_Salary <= 35000
```
