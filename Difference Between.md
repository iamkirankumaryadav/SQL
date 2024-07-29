# Difference Between

<table>
        <tr><th align=left><a href = '#dt'>1.DELETE vs TRUNCATE</a></th></tr>
        <tr><th align=left><a href = '#wh'>2.WHERE vs HAVING</a></th></tr>
        <tr><th align=left><a href = '#ua'>3.UNION vs UNION All</a></th></tr>
        <tr><th align=left><a href = '#pku'>4.PRIMARY KEY vs UNIQUE</a></th></tr>
        <tr><th align=left><a href = '#pkfk'>5.PRIMARY KEY vs FOREIGN KEY</a></th></tr>
        <tr><th align=left><a href = '#ie'>6.IN vs EXIST</a></th></tr>
        <tr><th align=left><a href = '#obgb'>7.ORDER BY vs GROUP BY</a></th></tr>
        <tr><th align=left><a href = '#jsq'>8.JOIN vs Sub Query</a></th></tr>
        <tr><th align=left><a href = '#uj'>9.UNION vs JOIN</a></th></tr>
        <tr><th align=left><a href = '#index'>10.INDEX</a></th></tr>
        <tr><th align=left><a href = '#cluster'>11.Clustered Index vs Non Clustered Index</a></th></tr>
        <tr><th align=left><a href = '#func'>12.Stored Procedure vs Function</a></th></tr>
        <tr><th align=left><a href = '#inner'>13.INNER JOIN vs OUTER JOIN</a></th></tr>
        <tr><th align=left><a href = '#lr'>13.LEFT JOIN vs RIGHT JOIN</a></th></tr>
</table>

<h3 name='dt'>1.DELETE vs TRUNCATE vs DROP</h3>

**DELETE** | **TRUNCATE** | **DROP**
:--- | :--- | :---
DML | DDL | DDL
Remove some or all rows | Remove all rows | Remove table from database
WHERE Clause | No WHERE Clause | No WHERE Clause
Roll Back | No Roll Back | No Roll Back
Doesn't removes permanently | Remove records permanently | Remove records, indexes, structures, metadata permanently

### **DELETE** 
```SQL 
DELETE FROM employee
WHERE employee_ID IN (1,2,3);
```

### **TRUNCATE**
```SQL
TRUNCATE TABLE employee;
```

### DROP 
```SQL
DROP TABLE employee;
```

<h3 name='wh'>2.WHERE vs HAVING</h3>

**WHERE** | **HAVING**
:--- | :---
Aggregate funtions are not allowed | Aggregate functions are allowed (SUM, AVG, MIN, MAX, COUNT)
Only supports filter conditions based on the existing columns | Support filters based on aggregated results 

- **HAVING** clause is used only after **GROUP BY** clause.
- **Aggregate Functions** are use to summarize data (Returns single aggregated value for multiple rows)

### **SUM | AVG | COUNT | MAX | MIN**

### **WHERE**
```SQL
SELECT * FROM employee
WHERE designation = 'Data Scientist';
```

### **HAVING**
```SQL
SELECT MAX(salary)
FROM employee
GROUP BY designation
HAVING MAX(salary) > 100000;
```

<h3 name='ua'>3.UNION vs UNION ALL</h3>

Combines 2 or more tables
- Tables must have same number of columns
- Columns must have same data type
- Columns must have same order of columns

**UNION** | **UNION ALL**
:--- | :---
Keep distinct records | Keep duplicate records

### **UNION**
```SQL
SELECT * FROM sales
UNION
SELECT * FROM product
ORDER BY product_name;
```

### **UNION ALL**
```SQL
SELECT * FROM sales
UNION ALL
SELECT * FROM product
ORDER BY product_name;
```

<h3 name='pku'>4.PRIMARY KEY vs UNIQUE</h3>

**Primary Key** | **Unique Key**
:--- | :---
We can have only one **PRIMARY KEY** in a table | We can have more than one **UNIQUE KEY** in a table
Do not accept **NULL** values | Accepts only one **NULL** value.
Identify UNIQUE rows in the table | Maintain UNIQUE data in a column.

### **PRIMARY KEY**

```SQL
CREATE TABLE person
(
    pID INT NOT NULL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,    
    age INT
);
```

### **UNIQUE KEY**

```SQL
CREATE TABLE person
(
    pID INT NOT NULL UNIQUE,
    name VARCHAR(255) NOT NULL,    
    age INT
);
```

<h3 name = 'pkfk'>5.PRIMARY KEY vs FOREIGN KEY</h3>

**PRIMARY KEY** | **FOREIGN KEY**
:--- | :---
Identify UNIQUE row in the table | Column in a table which is PRIMARY KEY in another table
We can have only one PRIMARY KEY in the table | We can have more than one FOREIGN KEY in the table
PRIMARY KEY can not accept NULL value | FOREIGN KEY accepts NULL values
PRIMARY KEY will not allow Duplicate value | FOREIGN KEY will allow duplicate value.

### **PRIMARY KEY**

```SQL
CREATE TABLE person
(
    pID INT NOT NULL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,    
    age INT
);
```

### **Unique Key**

```SQL
CREATE TABLE person
(
    pID INT NOT NULL UNIQUE,
    name VARCHAR(255) NOT NULL,    
    age INT
);
```

<h3 name='ie'>6.IN vs EXISTS</h3>

### **IN** 
- Multiple OR

```SQL
SELECT * FROM employee
WHERE city = 'Mumbai' OR city = 'Bangalore' OR city = 'Pune';
```

```SQL
SELECT * FROM employee
WHERE city IN (`Mumbai`, `Bangalore`, `Pune`);
```

```SQL
SELECT * FROM sales
WHERE city IN (SELECT city FROM returns)
```

### **EXISTS**
- Returns either True or False value (Tests for existance of records in a sub query)

```SQL
SELECT * FROM sales
WHERE EXISTS (SELECT city FROM returns
              WHERE returns.ID = sales.ID AND price < 500)
```

<h3 name='obgb'>7.ORDER BY vs GROUP BY</h3>

**ORDER BY** | **GROUP BY*
--- | ---
Sorting in **ASC** or **DESC** order | Used with **Aggregate** functions

### **ORDER BY**

```SQL
SELECT * FROM sales
ORDER BY city DESC;
```

### **GROUP BY**
```SQL
SELECT is_active, COUNT(*)
FROM customers
GROUP BY is_active;
```

**WHERE** Clause is used with **SELECT** Clause before **GROUP BY**
```SQL
SELECT designation, salary 
FROM employee
WHERE designation IN ('Data Scientist', 'Data Analyst', 'Business Analyst', 'Data Architect', 'Machine Learning Engineer')
GROUP BY designation;
```

**HAVING** Clause is used with **GROUP BY** and **WHERE** Clause can't be used after **GROUP BY**
```SQL
SELECT model, price 
FROM vehicles
GROUP BY model
HAVING SUM(price) > 5000000
ORDER BY price DESC;
```

<h3 name='jsq'>8.JOIN vs Sub Query</h3>

Combine data from different tables into a single table

### **Sub Query**

```SQL
-- Select only from first table:
SELECT phone, customer_name
FROM customer
WHERE c_ID IN (SELECT c_ID 
               FROM orders)
```

### **JOIN**

```SQL
-- Select from either of the table:
SELECT phone, customer_name, order_ID
FROM customers c
JOIN orders o
ON o.customer_ID = c.customer_ID
```

<h3 name='uj'>9.UNION vs JOIN</h3>

**UNION** | **JOIN**
:--- | :---
Combine rows | Merge columns  
Number of columns and data type of columns should be same | Combines on the basis of common column (ID/Values)
Vertical | Horizontal

### **UNION** 
```SQL
SELECT city from table1
UNION
SELECT city from table2;
```

### **JOIN**
```SQL
SELECT a.city, b.name
FROM departments a
JOIN employee b
ON a.ID = b.ID;
```

<h3 name='index'>10.Index</h3>

- Index are used for fast retrieval of data.
- Index in the database is very similar to an Index in a book.
- e.g. If you want to refer to a pages in a book, you first refer to the Index.

### **Types of Indexes**

**Single Column Index:** Index based on only one column.

```SQL
CREATE INDEX index_name 
ON table_name (column_name);
```

**Unique Index:** Does not allow any duplicate values to be inserted into the table.

```SQL
CREATE UNIQUE INDEX index_name
ON table_name (column_name);
```

**Composite Indexes:** An Index on two or more columns of a table.

```SQL
CREATE INDEX index_name
ON table_name (column_name1, column_name2);
```     

**Implicit Indexes:** Index automatically created by PRIMARY KEY constraint and UNIQUE constraint when an object is created.

<h3 name='cluster'>11.Clustered Index vs Non Clustered Index</h3>

#### **Clustered Index**

- Defines the order in which data is physically stored in a table.
- When we create a table with ID as PRIMARY KEY, this automatically creates Clustered Index.

#### **Non Clustered Index**

- Doesn't sort the physical data inside the table.
- Non Clustered Index is stored at different place then the table data.
- e.g. Textbook content | Index is located on first page but the actual content is all at different pages.
- Index contains column value and address of the record.

<h3 name='func'>12.Stored Procedure vs Function</h3>

**Stored Procedure** | **Function**
:--- | :---
Stored procedure can return 0 or N values | Function must return a value
Can have multiple Input as well as Output parameters | Can have only one Input parameter
Procedures cannot be called from function | Functions can be called from procedure

<h3 name='inner'>13.Inner Join vs Outer Join</h3>

**Inner Join** | **Outer Join**
:--- | :---
Return only matching rows between both the tables | Returns matching and unmatching rows between both the tables
Default Join | It is not a Default Join

<h3 name='lr'>14.Left Join vs Right Join</h3>

**Left Join** | **Right Join**
:--- | :---
Return all the rows from the left table  | Return all the rows from the right table  
Return only the matching rows from the right table | Return only the matching rows from the left table

