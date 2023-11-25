# Queries

### `Constraints` : Rules and Validations

```
1. PRIMARY KEY  : A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table.
2. FOREIGN KEY  : Prevents actions that would destroy links between tables.
3. UNIQUE       : Ensures that all values in a column are different.
4. NOT NULL     : Ensures that a column cannot have a NULL value.
5. CHECK        : Ensures that the values in a column satisfies a specific condition.
6. DEFAULT      : Sets a default value for a column if no value is specified.
7. CREATE_INDEX : Used to create and retrieve data from the database very quickly.
```

```SQL
-- PRIMARY KEY:
CREATE TABLE Employee
(
  ID INT NOT NULL PRIMARY KEY,
  Name VARCHAR(255)
);

-- FOREIGN KEY:
CREATE TABLE Employee
(
  EID INT NOT NULL PRIMARY KEY,
  Name VARCHAR(255),
  DID INT NOT NULL FOREIGN KEY REFERENCES Department(DID)
)

-- UNIQUE:
ALTER TABLE Employee
ADD UNIQUE(ID);

-- NOT NULL:
CREATE TABLE Employee
(
  ID           INT NOT NULL,
  EmployeeName VARCHAR(255) NOT NULL
);

ALTER TABLE Employee
MODIFY EmployeeName NOT NULL;

-- CHECK:
CREATE TABLE Employee
(
  ID INT NOT NULL,
  Age INT CHECK(AGE >= 18)
);
```

### `Aggregate` Functions 

```
1. SUM()   : Returns a total
2. AVG()   : Returns the averages of numbers.
3. MIN()   : Returns the lowest or oldest (date)
4. MAX()   : Returns the highest or newest (date)
5. COUNT() : Returns the numbers of values (frequency)
```

### SQL `Categorization` 

```
1. DDL : Data Definition Language
2. DML : Data Manipulation Language
3. DCL : Data Control Language
4. TCL : Transaction Control Language
5. DQL : Data Query Language
```

### `Relationship` types in SQL ?

```
1. One to One   : One person can choose one stream. 
2. One to Many  : One teacher can teach many subjects.
3. Many to Many : Many students can learn many subjects.
```

### `UNION` vs `UNION ALL`
- Number of the columns, data type and order of the columns should be same.
- `UNION` keeps only `DISTINCT` where as `UNION ALL` preserves duplicates.

### Select All 
- Select `all` columns of the Table.

```SQL
SELECT * FROM Table;
```

### Select Columns 
- Select `specific` columns from the Table.

```SQL
SELECT Column1, Column2, Column3 
FROM Table;
```	

### Select Distint 
- Select `Unique` value of the specified Column from the Table.

```SQL
SELECT DISTINCT Column 
FROM Table;
```

### Select Count 
- Total Number of `Rows`.

```SQL
SELECT COUNT(DISTINCT Column) 
FROM Table;
```

### Select Condition  

```SQL
SELECT * FROM Table 
WHERE Column = Value;
```

### Select Between (Range)

```SQL
SELECT * 
FROM Students 
WHERE Age BETWEEN 8 AND 16;
```

### Select Like ( Pattern )  

```SQL
SELECT * 
FROM Employee 
WHERE Name LIKE 'K%';
```

1. 'K%'    : Starts with K
2. '%K'    : Ends with K
3. '%K%'   : K at any Position
4. '_K%'   : K at Second Position
5. 'A___%' : Four Letter Words Starting with A
6. 'K%V'   : Starting with K and Ending with V
7. '[ABC]%': Starting with A, B and C
8. '[!AB]%': Not Starting with A and B

### Select In (Specific Value)

```SQL
SELECT * 
FROM Sales 
WHERE State IN ('Maharashtra', 'Banglore');
```

### Select Null 

```SQL
SELECT * 
FROM Shop 
WHERE Sale IS NULL
```

### Select Not Null 

```SQL
SELECT * 
FROM Shop 
WHERE Sale IS NOT NULL
```

### Select And 

```SQL
SELECT * 
FROM Sales 
WHERE State = "Maharashtra" AND City = "Mumbai";
```

### Select Or 

```SQL
SELECT * 
FROM Sales 
WHERE State = "Maharashtra" OR City = "Mumbai";
```

### Select And + Or 

```SQL
SELECT * 
FROM Sales
WHERE State = "Maharashtra" AND ( City = "Mumbai" OR City = "Pune" );
```

### Select Not  

```SQL
SELECT * 
FROM Sales 
WHERE NOT City = "Mumbai";
```

### Select Not And 

```SQL
SELECT * 
FROM Sales 
WHERE NOT City = "Mumbai" AND NOT City = "Pune";
```

### Select Order By  
- `Sort`Table by Column in Ascending and Descending Order. 

```SQL
SELECT State, City
FROM Sales 
ORDER BY State DESC, City ASC;
```

### Insert 
- Add Row 

```SQL
INSERT INTO TableName(Column1, Column2, Column3) 
VALUES(Value1, Value2, Value3); 
```

### Update 

```SQL
UPDATE TableName 
SET Column1 = Value1, Column2 = Value2 
WHERE Condition;
```

### Delete 

```SQL
DELETE FROM TableName 
WHERE Column = Value;
```

### Select Top 

```SQL
SELECT TOP 10 * 
FROM TableName; 
```

```SQL
SELECT * 
FROM TableName 
LIMIT = 10;
```

### Select Aggregate 

1. `COUNT()` : Total number of `Rows`.
2. `AVG()` : Average | Mean
3. `SUM()` : Addition of all the values.
4. `MIN()` : Smallest value.
5. `MAX()` : Largest value.

```SQL
SELECT SUM(Column) AS SumColumn 
FROM Table WHERE Column = A;
```

Aggregate Function + Group By + Having
```sql
SELECT state, COUNT(*) AS total_customers
FROM customers
GROUP BY state
HAVING COUNT(*) > 100;
```

# `Joins`

1. `Inner` Join : Matching `Rows` in both Table.
2. `Left` Join : `All` the Rows from Left Table and Matching Rows from Right Table.
3. `Right` Join : `All` the Rows from Right Table and Matching Rows from Left Table.
4. `Full` Join | Full Outer Join : `All` the Rows from both the Table.

### `Inner` Join  

```SQL
SELECT Table1.Column1, Table1.Column2, Table1.Column3 
FROM Table1 
INNER JOIN Table2 ON Table1.ID = Table2.ID
```

### `Join` multiple tables: 

```SQL
SELECT Table1.Column1, Table2.Column2, Table3.Column3 
FROM Table1 
INNER JOIN Table2 ON Table1.ID = Table2.ID 
INNER JOIN Table3 ON Table1.ID = Table3.ID
```

### `Union` (Distinct)
- `Combine` Tables and Subsets (Combines only `Distinct` Rows)

```SQL
SELECT Column1, Column2, Column3 
FROM Table1 
UNION 
SELECT Column1, Column2, Column3 
FROM Table2
```

### Union + Condition 

```SQL
SELECT Column1, Column2, Column3 
FROM Table1 
WHERE Column1 = A 
UNION 
SELECT Column1, Column2, Column3 
FROM Table2 
WHERE Column1 = B 
ORDER BY Column1
```

### `UNION All`  
- `Combine` Tables and Subsets (Combines `All` Rows)

```SQL
SELECT Column1, Column2, Column3 
FROM Table1 
UNION ALL 
SELECT Column1, Column2, Column3 
FROM Table2
```

### `GROUP BY`
- Group `Rows` with same value.

```SQL
SELECT Country, COUNT(Customer) 
FROM Sales 
GROUP BY Country;
```

```SQL
SELECT Country, COUNT(Customer) 
FROM Sales 
GROUP BY Country 
ORDER BY Count(Customer) DESC;
```

### Join + Group By 

```SQL
SELECT Table1.Column1, Count(Table1.ID) 
FROM Table1 
LEFT JOIN Table2 ON Table1.ID = Table2.ID 
GROUP BY Column1;
```

### Join + Group By + Having 

```SQL
SELECT Table1.Column1, Count(Table1.ID) 
FROM Table1 
INNER JOIN Table2 ON Table1.ID = Table2.ID
WHERE Column1 = 'A' And Column2 = B
GROUP BY Table1.Column1
HAVING Count(Table1.ID) > 20
ORDER BY Count(Table1.ID) DESC;
```
                            
### Where Exists   
- Test for the Existence of any `Row` in a Sub Query.

```SQL
SELECT Column1 
FROM Table1 
WHERE EXISTS(SELECT Column2 FROM Table2 WHERE Table2.ID = Table1.ID)
```

### Select Any 
- Returns `True` if the operation is `True` for any of the value.

```SQL
SELECT ProductName
FROM Products 
WHERE ProductID = ANY(SELECT ProductID FROM Orders WHERE Quantity = 'Value')
```

### Select All 
- Returns `True` if the operation is `True` for all of the value.

```SQL
SELECT ProductName
FROM Products 
WHERE ProductID = ALL(SELECT ProductID FROM Orders WHERE Quantity = 'Value')
```

### Select Into 

```SQL
SELECT * INTO NewTableName 
FROM OldTableName 
WHERE Column = B;
```

```SQL
SELECT * INTO IndianCustomer 
FROM Customers 
WHERE Country = 'India';
```

### Insert Into : 

```SQL
INSERT INTO Table2(Colum1, Column2, Column3) 
SELECT Column1, Column2, Column3 
FROM Table1
WHERE Column1 = Value;
```	

### SQL Case   

```SQL
SELECT OrderID, Quantity,
CASE
    WHEN Quantity = 30 THEN 'Quantity is Matching'
    WHEN Quantity < 30 THEN 'Quantity is Less than 30'
    ELSE 'Quantity is More than 30'
END 
AS QuantityMessage
FROM OrderDetails;
```

### Select Null : 

`IFNULL` (Column, Value) : If Value is NULL Replace it by 0 

```SQL
SELECT Product, IFNULL(Price, 0) 
FROM Products.
```

### Sql Constraints

1. `NOT NULL` : Enforces a column to not accept any null value.
2. `AUTO_INCREMENT` : Automatically generate sequential numbers.
3. `PRIMARY KEY` : Uniquely identify the `row` in the table.
4. `FOREIGN KEY` : Primary key in another table.
5. `CHECK` : `Limit` the value range that can be placed in a column.
6. `DEFAULT` : Set a `Default` value for the column.

```SQL
CREATE TABLE Employee
(
      ID     INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
      Name   VARCHAR(255),
      Age    INT CHECK(Age > 18),
      DeptID INT NOT NULL FOREIGN KEY REFERENCES Department(DeptID),
      City   VARCHAR(255) DEFAULT 'Mumbai'
)
```

### Sql Views
- `Virtual` table that contains data from one or more table.

```SQL
CREATE VIEW [Indian Customer] AS
SELECT CustomerName, ContactNumber
FROM Customers
WHERE Country = 'India';
```


```SQL
CREATE VIEW [Over Price] AS 
SELECT ProductName, Price
FROM Product
WHERE Price > (SELECT AVG(Price) FROM Product);
```

### Sub Queries | Inner Query | Nested Query
- A Query within another SQL Query.

```SQL
SELECT * 
FROM Employees
WHERE ID IN (SELECT ID FROM Employees WHERE Salary > 50000);
```

### Extract String

```SQL
SELECT LEFT("Kirankumar Yadav", 10);
------------------------------------
Output : Kirankumar

SELECT RIGHT('Kirankumar Yadav', 5);
------------------------------------
Output : Yadav

SELECT MID("Aspiring Data Scientist", 10, 4)
--------------------------------------------
Output : Data

SELECT CONCAT("Data ", "Science ", "and ", "Artificial ", "Intelligence")
-------------------------------------------------------------------------
Output : Data Science and Artificial Intelligence
```   

<p align='right'><a align="right" href="https://github.com/KIRANKUMAR7296/Library/blob/main/Interview.md">Back to Questions</a></p>
