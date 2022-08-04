# Queries

1. Query the List of City Names from A Table that do not Start with `Vowels` and do not End with `Vowels` + Result cannot contain Duplicates.

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
