# **Data Query Language (DQL)**

Fetch the data from the database. SELECT the data based on the conditions described by the WHERE clause.

Operators | Description
--- | ---
SELECT | Retrieve data from a database.
WHERE | Filter rows based on a specified condition.
ORDER BY | Sort the result set in ascending or descending order.
GROUP BY | Groups rows based on the values in a specified column.
HAVING | Filters grouped results based on a specified condition.
BETWEEN | Returns data within a range of values.
IN | Returns data within a list of values.
ANY | Compare a value to any value returned by a subquery.
ALL | Compare a value to all values returned by a subquery.
LIKE | Returns data similar to the given pattern (Using Wildcard)
IS NULL | Returns null values.
IS NOT NULL | Returns not null values.
EXISTS | Determine if a subquery returns values or not.

### **SELECT Statement**

```sql
SELECT first_name, last_name
FROM Customers;
```

### **WHERE Clause**

```sql
SELECT * FROM Customers
WHERE age > 30;
```

### **ORDER BY Clause**

```sql
SELECT * FROM products
ORDER BY price DESC;
```

### **GROUP BY**

```sql
SELECT category, COUNT(*)
FROM products
GROUP BY category;
```

### **HAVING Clause**

```sql
SELECT category, COUNT(*)
FROM products
GROUP BY category
HAVING count(*) > 5;
```    

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

### **IN**

```sql
SELECT * FROM customers
WHERE city IN (SELECT city from suppliers)
```

### **ANY**

```sql
SELECT * FROM products
WHERE price < ANY(SELECT unit_price
                  FROM supplier_products)
```

### **ALL**

```sql
SELECT * FROM orders
WHERE order_amount > ALL(SELECT total_amount
                         FROM previous_orders)
```

### **COALESCE**

```sql
# Return the first non-null value in the list:
SELECT First_Name, Last_Name, Starting_Salary, Current_Salary, 
COALESCE(Current_Salary*1.1, Starting_Salary) AS New_Salary 
FROM Employee
WHERE Starting_Salary <= 35000
```
