# Queries

1. Query the list of city names from a table that do not start with `vowels` and do not end with `vowels` + result cannot contain duplicates.

`SUBSTRING(Column, Index, Length)`

```SQL
SELECT DISTINCT City 
FROM Employee
WHERE SUBSTRING(City, 1, 1) NOT IN ('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U')
AND SUBSTRING(City, -1, 1) NOT IN ('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U');
```

2. Query Name of Students who Scored Higher than `75` Marks, Order by the Last `3` Characters of Each Name.

( If `2` or more Students both have Names ending in the Same Last `3` Characters ( i.e. Kavya, Navya, etc ) Sort them by ID in Ascending Order )

```SQL
SELECT Name 
FROM Students
WHERE Marks > 75
ORDER BY SUBSTRING(Name, -3, 3), ID;
```

3. Query an Alphabetically Ordered List of all Names, Immediately followed by `First` Character enclosed in Paranthesis.

Name | Occupation
--- | ---
Jake | Doctor
Alan | Actor
Charlie | Singer

```SQL
SELECT CONCAT(Name, '(', SUBSTRING(Occupation, 1, 1), ')')
FROM Occupation;
```

```
Output : 
Jake (D)
Alan (A)
Charlie (S)
```

4. Query to Fetch All Employees who is also a Managers from Employee Table

```SQL
SELECT DISTINCT EmployeeID
FROM Employee E
INNER JOIN Employees M
ON E.EmployeeID = M.EmployeeID
```

5. `2nd` Highest Salary

```SQL
--- Query 1:
SELECT * FROM ((SELECT * FROM Employee ORDER BY Salary DESC Limit 2) AS T)
ORDER BY T.Salary ASC Limit 1;

-- Query 2:
SELECT Salary 
FROM (SELECT Salary FROM Employee ORDER BY Salary DESC LIMIT 2)
AS Emp
ORDER BY Emp.Salary LIMIT 1;

-- Query 3:
SELECT TOP 1 Salary 
FROM (SELECT TOP 2 Salary FROM Employee ORDER BY Salary DESC)
AS Emp
ORDER BY Emp.Salary ASC;

-- Query 4: 
SELECT MAX(Salary) 
FROM Employee
WHERE Salary < (SELECT MAX(Salary) FROM Employee);
```

6. `5th` Highest Salary

```SQL
SELECT * FROM ((SELECT * FROM Employee ORDER BY Salary DESC Limit 5) AS T)
ORDER BY T.Salary ASC Limit 1;
```

7. Select count of employee hired every month and year
```sql
SELECT MONTH(Employee.StartDate), YEAR(Employee.StartDate), COUNT(1)
FROM Employee
GROUP BY MONTH(Employee.StartDate), YEAR(Employee.StartDate)
ORDER BY 1, 2
```

8. Select employee active on given date:
```sql
SELECT * FROM Employee
WHERE Employee.StartDate <= '2021-07-01'                           -- Before 1st July 2021
AND (Employee.EndDate >= '2021-07-01' OR Employee.EndDate IS NULL) -- After 1st July 2021  
```

9. How to get next month and last day of current month:
```sql
SELECT
Dates.DateKey,
DATE_TRUNC(Dates.DateKey, "month") Month,
DATE_ADD(DATE_TRUNC(Dates.DateKey, "month"), 1, "month") Next_Month,
DATE_ADD(DATE_ADD(DATE_TRUNC(Dates.DateKey, "month"), 1, "month"), -1, "day") End_of_Month
FROM Dates
LIMIT 10;
```

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
