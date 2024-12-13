# Data Query Language (DQL)

Fetch the data from the database. **SELECT** the data based on the conditions described by the WHERE clause.

**Operators** | **Description**
--- | ---
**SELECT** | Retrieve data from a database.
**WHERE** | Filter rows based on a specified condition.
**ORDER BY** | Sort the result set in ascending or descending order.
**GROUP BY** | Groups rows based on the values in a specified column.
**HAVING** | Filters grouped results based on a specified condition.
**BETWEEN** | Returns data within a range of values.
**IN** | Returns data within a list of values.
**ANY** | Compare a value to any value returned by a subquery.
**ALL** | Compare a value to all values returned by a subquery.
**LIKE** | Returns data similar to the given pattern (Using Wildcard)
**IS NULL** | Returns null values.
**IS NOT NULL** | Returns not null values.
**EXISTS** | Determine if a subquery returns values or not.

### SELECT Statement
```sql
SELECT first_name, last_name
FROM employee;
```

### WHERE Clause
```sql
SELECT * FROM employee
WHERE age > 30;
```

### ORDER BY Clause
```sql
SELECT * FROM products
ORDER BY price DESC;
```

### GROUP BY
```sql
SELECT category, COUNT(*)
FROM products
GROUP BY category;
```

### HAVING Clause
```sql
SELECT category, COUNT(*)
FROM products
GROUP BY category
HAVING COUNT(*) > 5;
```    

### Querying the table with the logical operator LIKE:
```sql
-- Underscore: _

SELECT code
FROM table
WHERE code LIKE '_2_6'

Results :
'1216'
'1226'
'1236'...
```

```sql
-- Square Brackets: [ ] | or

SELECT last_name 
FROM employee
WHERE last_name LIKE 'Wi[lk]%' -- 'Wi' followed by either 'l' or 'k'

Results :
'Williams'
'Wilson'
'Wikson'
```

```sql
-- Percentage: %  

-- Get only Google mails:
SELECT first_name, email 
FROM employee
WHERE email LIKE '%@gmail.com'

------------------------------
-- Get emails other than Gmail:
SELECT first_name, email
FROM employee
WHERE email NOT LIKE '%@gmail.com' 

----------------------------------

SELECT first_name, city
FROM employee
WHERE first_name LIKE 'B[iro]%' AND City NOT LIKE '%UL%'
```

### Querying the table with logical operators IN and BETWEEN
```sql
SELECT first_name, shirt_size 
FROM customer
WHERE shirt_size IN ('M', 'L', 'XL', 'XXL')
ORDER BY shirt_size ASC
```

```sql
SELECT first_name, pant_size, DATENAME(Month, birthday) as birth_month 
FROM customer
WHERE pant_size BETWEEN 2 AND 16 AND shirt_size LIKE '%L'
ORDER BY birth_month
```

```sql
SELECT first_name, DATENAME(Year, birthday) as birth_year 
FROM customer
WHERE birthday BETWEEN '1980' AND '1982'
ORDER BY birth_year DESC
```

### IN
```sql
SELECT * FROM customers
WHERE city IN (SELECT city from suppliers)
```

### ANY
```sql
SELECT * FROM products
WHERE price < ANY(SELECT unit_price
                  FROM supplier_products)
```

### ALL
```sql
SELECT * FROM orders
WHERE order_amount > ALL(SELECT total_amount
                         FROM previous_orders)
```

### COALESCE
```sql
-- Return the first non-null value in the list:
SELECT first_name, last_name, starting_salary, current_salary, 
COALESCE(current_salary * 1.1, starting_salary) AS new_salary 
FROM employee
WHERE starting_salary <= 35000
```
