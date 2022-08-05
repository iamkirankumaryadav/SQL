# Difference Between

<table>
        <tr><th align=left><a href = '#dt'>1. Delete vs Truncate</a></th></tr>
        <tr><th align=left><a href = '#wh'>2. Where vs Having</a></th></tr>
        <tr><th align=left><a href = '#ua'>3. Union vs Union All</a></th></tr>
        <tr><th align=left><a href = '#pku'>4. Primary Key vs Unique</a></th></tr>
        <tr><th align=left><a href = '#pkfk'>5. Primary Key vs Foreign Key</a></th></tr>
        <tr><th align=left><a href = '#ie'>6. In vs Exist</a></th></tr>
        <tr><th align=left><a href = '#obgb'>7. Order By vs Group By</a></th></tr>
        <tr><th align=left><a href = '#jsq'>8. Join vs Sub Query</a></th></tr>
        <tr><th align=left><a href = '#uj'>9. Union vs Join</a></th></tr>
        <tr><th align=left><a href = '#index'>10. Index</a></th></tr>
        <tr><th align=left><a href = '#cluster'>11. Clustered Index vs Non Clustered Index</a></th></tr>
        <tr><th align=left><a href = '#func'>12. Stored Procedure vs Function</a></th></tr>
        <tr><th align=left><a href = '#inner'>13. Inner Join vs Outer Join</a></th></tr>
        <tr><th align=left><a href = '#lr'>13. Left Join vs Right Join</a></th></tr>
</table>

<h3 name='dt'>1. Delete vs Truncate vs Drop</h3>

DELETE | TRUNCATE | DROP
--- | --- | ---
DML | DDL | DDL
Remove `Some` or `All` Rows | Remove `All` Rows | Remove `Table` from Database
WHERE Clause | `No` WHERE Clause | `No` WHERE Clause
Roll Back | `No` Roll Back | `No` Roll Back
Do not Remove Permanently | Remove Records Permanently | Remove Records, Indexes, Structures Permanently

### DELETE 
```SQL 
DELETE FROM Employee
WHERE EID IN (1,2,3);
```

### TRUNCATE
```SQL
TRUNCATE Table Employee;
```

### DROP 
```SQL
DROP Table Employee;
```

<h3 name='wh'>2. Where vs Having</h3>

WHERE | HAVING
--- | ---
`Filter` Rows | Works on `Aggregated` Data

**Aggregate Functions** are use to `Summarize` Data ( Returns Single Value for Multiple Rows )

### SUM | AVG | COUNT | MAX | MIN

### WHERE
```SQL
SELECT * 
FROM Employee
WHERE Designation = 'Data Scientist';
```

### HAVING
```SQL
SELECT MAX(Salary)
FROM Employee
GROUP BY Designation
HAVING MAX(Salary) > 100000;
```

<h3 name='ua'>3. Union vs Union All</h3>

Combines `2` or `more` Tables
- Tables must have same Number of `Columns`
- Columns must have same `Data Types`
- Columns must have same `Order`

UNION | UNION
`Remove` Duplicate Records | `Keep` Duplicate Records

### UNION
```SQL
SELECT * FROM Sales
UNION
SELECT * FROM Product
ORDER BY ProductName;
```

### UNION ALL
```SQL
SELECT * FROM Sales
UNION ALL
SELECT * FROM Product
ORDER BY ProductName;
```

<h3 name='pku'>4. Primary Key vs Unique</h3>

Primary Key | Unique Key
:--- | :---
We can have only one Primary Key in a Table | We can have more than one Unique Key in a Table
Do not accept `NULL` Value | Accepts only `One` Null Value.
Identify Unique `Row` from Table | Maintain Unique `Data` in a Column.

### Primary Key

```SQL
CREATE TABLE Person
(
    ID INT NOT NULL PRIMARY KEY,
    Name VARCHAR(255) NOT NULL,    
    Age INT
);
```

### Unique Key

```SQL
CREATE TABLE Person
(
    ID INT NOT NULL UNIQUE,
    Name VARCHAR(255) NOT NULL,    
    Age INT
);
```

<h3 name = 'pkfk'>5. Primary Key vs Foreign Key</h3>

Primary Key | Foreign Key
:--- | :---
Identify Unique `Row` in the Table | Column in a Table which is Primary Key in another Table
We can have only one Primary Key in the Table | We can have more than one Foreign Key in the Table
Primary Key can not accept NULL Value | Foreign Key Accepts NULL Value
Primary Key will not allow Duplicate Value | Foreign Key will allow Duplicate Value.

### Primary Key

```SQL
CREATE TABLE Person
(
    ID INT NOT NULL PRIMARY KEY,
    Name VARCHAR(255) NOT NULL,    
    Age INT
);
```

### Unique Key

```SQL
CREATE TABLE Person
(
    ID INT NOT NULL UNIQUE,
    Name VARCHAR(255) NOT NULL,    
    Age INT
);
```

<h3 name='ie'>6. In vs Exist</h3>

### IN 
- Multiple `OR`

```SQL
SELECT * FROM Employee
WHERE City = 'Mumbai' OR City = 'Bangalore' OR City = 'Pune';
```

```SQL
SELECT * FROM Employee
WHERE City IN (`Mumbai`, `Bangalore`, `Pune`);
```

```SQL
SELECT * FROM Sales
WHERE City IN (SELECT City FROM Returns)
```

### EXISTS
- Returns either `True` or `False` Value ( Tests for Existance of Record in a Sub Query )

```SQL
SELECT * FROM Sales
WHERE EXISTS (SELECT City FROM Returns
              WHERE Returns.ID = Sales.ID AND Price < 500)
```

<h3 name='obgb'>7. Order By vs Group By</h3>

ORDER BY | GROUP BY
--- | ---
Sorting in `ASC` or `DESC` Order | Used with `Aggregate` Functions

### ORDER BY

```SQL
SELECT * FROM Sales
ORDER BY City 
DESC;
```

### GROUP BY
```SQL
SELECT IsActive, COUNT(*)
FROM Customers
GROUP BY IsActive;
```

WHERE Clause is Used with SELECT Clause before GROUP BY
```SQL
SELECT Designation, Salary 
FROM Employee
WHERE Designation IN ('Data Scientist', 'Data Analyst', 'Business Analyst', 'Data Architect', 'Machine Learning Engineer')
GROUP BY Designation;
```

HAVING Clause is used with GROUP BY and WHERE Clause `cannot` be used after GROUP BY
```SQL
SELECT Model, Price 
FROM Vehicles
GROUP BY Model
HAVING SUM(Price) > 5000000
ORDER BY Price DESC;
```

<h3 name='jsq'>8. Join vs Sub Query</h3>

`Combine` Data from Different Tables into a Single Table

### Sub Query

Select only from `First` Table

```SQL
SELECT Phone, CustomerName
FROM Customers
WHERE C_ID IN (SELECT C_ID 
               FROM Orders)
```

### JOIN

Select from `Either` of the Table

```SQL
SELECT Phone, CustomerName, OrderID
FROM Customers C
JOIN Orders O
ON O.CustomerID = C.CustomerID
```

<h3 name='uj'>9. Union vs Join</h3>

UNION | JOIN
--- | ---
`Combine` Rows | `Merge` Columns  
Number of `Columns` and Data Type of Columns should be same | Combines on the basis of Common `Column` ( ID )
`Vertical` | `Horizontal`

### UNION 
```SQL
SELECT City from Table1
UNION
SELECT City from Table2;
```

### JOIN
```SQL
SELECT A.City, B.Name
FROM Departments A
JOIN Employee B
ON A.ID = B.ID;
```

<h3 name='index'>10. Index</h3>

- `Index` are used for fast retrieval of data.
- Index in the Database is very similar to an Index in the back of a book.
- e.g. If you want to Refer to a pages in a book, you first refer to the `Index`.

### Types of Indexes

#### Single Column Index
- Index based on only `One` Column.

```SQL
CREATE INDEX IndexName 
ON TableName (ColumnName);
```

#### Unique Index
- Does not allow any `Duplicate` Values to be inserted into the table.

```SQL
CREATE UNIQUE INDEX IndexName
ON TableName (ColumnName);
```

#### Composite Indexes
- An Index on Two or More Columns of a Table.

```SQL
CREATE INDEX IndexName
ON TableName (ColumnName1, ColumnName2);
```     

#### Implicit Indexes
- Index Automatically created by `Primary Key` Constraints and `Unique` Constraints when an Object is created.

<h3 name='cluster'>11. Clustered Index vs Non Clustered Index</h3>

#### Clustered Index

- Defines the `Order` in which Data is Physically stored in a Table.
- When we Create a Table with ID as `PRIMARY KEY`, this Automatically creates Clustered Index.

#### Non Clustered Index

- Doesn't `Sort` the Physical Data inside the Table.
- Non Clustered Index is stored at different place then the Table Data.
- e.g. Textbook content | Index is located on first page but the actual content is all at different pages.
- Index contains column value and Address of the Record.

<h3 name='func'>12. Stored Procedure vs Function</h3>

Stored Procedure | Function
:--- | :---
Stored Procedure can return `0` or `N` Values | Function must return a `Value`
Can have Multiple `Input` as well as `Output` Parameters | Can have only One `Input` Parameter
Procedures cannot be called from `Function` | Functions can be called from `Procedure`

<h3 name='inner'>13. Inner Join vs Outer Join</h3>

Inner Join | Outer Join
:--- | :---
Return Only `Matching` Rows between both the Tables | Returns `Matching` and `Unmatching` Rows between both the Tables
`Default` Join | It is not a Default Joint 

<h3 name='lr'>14. Left Join vs Right Join</h3>

Left Join | Right Join
:--- | :---
Return `All` the Rows from `Left` Table  | Return `All` the Rows from `Right` Table  
Return Only `Matching` Rows from the `Right` Table | Return Only `Matching` Rows from the `Left` Table

