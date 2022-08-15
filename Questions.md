# Common SQL Questions :

### 1. When and how might you use an **alias** ?
```sql
SELECT S.Last_Name, 
COUNT(S.Last_Name) 
AS TotalStudents
FROM Students S
```

### 2. `Clause` in SQL Queries.

```sql
SELECT S.First_Name, S.Last_Name, S.Department, Count(S.Class)
FROM Staff S
WHERE S.Last_Name LIKE '%ol%'
ORDER BY S.Last_Name
HAVING Count(S.Class) > 5
GROUP BY S.Department DESC
```
```
1. SELECT   : Select the columns.
2. FROM     : Where the data is coming from ? (Which Table)
3. WHERE    : Filter out the data.
4. ORDER BY : Column which we will be using to sort the data. 
5. HAVING   : What characteristics ? (Usually used in Aggregate Function)
6. GROUP BY : Always follows the HAVING Clause.
```

### 3. What is the order of execution for a `SELECT` statment ?

```
# Query Order of Execution :

FROM     : Where data is coming from ?
WHERE    : How to filter out the data ?
GROUP BY : How data is grouped ?
HAVING   : Which Characteristics ?
SELECT   : What data is returned ?
ORDER BY : How data is started ?
```

### 4. Query the list of city names from a table that do not start with `vowels` and do not end with `vowels` + result cannot contain duplicates.

`SUBSTRING(Column, Index, Length)`

```SQL
SELECT DISTINCT City 
FROM Employee
WHERE SUBSTRING(City, 1, 1) NOT IN ('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U')
AND SUBSTRING(City, -1, 1) NOT IN ('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U');
```

### 5. Query Name of Students who Scored Higher than `75` Marks, Order by the Last `3` Characters of Each Name.

( If `2` or more Students both have Names ending in the Same Last `3` Characters ( i.e. Kavya, Navya, etc ) Sort them by ID in Ascending Order )

```SQL
SELECT Name 
FROM Students
WHERE Marks > 75
ORDER BY SUBSTRING(Name, -3, 3), ID;
```

### 6. Query an Alphabetically Ordered List of all Names, Immediately followed by `First` Character enclosed in Paranthesis.

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

### 7. Query to Fetch All Employees who is also a Managers from Employee Table

```SQL
SELECT DISTINCT EmployeeID
FROM Employee E
INNER JOIN Employees M
ON E.EmployeeID = M.EmployeeID
```

### 8. `2nd` Highest Salary

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

### 9. `5th` Highest Salary

```SQL
SELECT * FROM ((SELECT * FROM Employee ORDER BY Salary DESC Limit 5) AS T)
ORDER BY T.Salary ASC Limit 1;
```

### 10. Select count of employee hired every month and year

```sql
SELECT MONTH(Employee.StartDate), YEAR(Employee.StartDate), COUNT(1)
FROM Employee
GROUP BY MONTH(Employee.StartDate), YEAR(Employee.StartDate)
ORDER BY 1, 2
```

### 11. Select employee active on given date:

```sql
SELECT * FROM Employee
WHERE Employee.StartDate <= '2021-07-01'                           -- Before 1st July 2021
AND (Employee.EndDate >= '2021-07-01' OR Employee.EndDate IS NULL) -- After 1st July 2021  
```

### 12. How to get next month and last day of current month:

```sql
SELECT
Dates.DateKey,
DATE_TRUNC(Dates.DateKey, "month") Month,
DATE_ADD(DATE_TRUNC(Dates.DateKey, "month"), 1, "month") Next_Month,
DATE_ADD(DATE_ADD(DATE_TRUNC(Dates.DateKey, "month"), 1, "month"), -1, "day") End_of_Month
FROM Dates
LIMIT 10;
```
