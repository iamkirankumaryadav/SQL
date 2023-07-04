# JOINS

<table>
        <tr>
                <th align=left><a href = '#inner'>1. Inner Join</a></th>
                <th align=left><a href = '#left'>2. Left Join</a></th>
                <th align=left><a href = '#right'>3. Right Join</a></th>
                <th align=left><a href = '#self'>4. Self Join</a></th>
                <th align=left><a href = '#outer'>5. Outer Join</a></th>
        </tr>
        <tr>
                <th align=left colspan=2><a href = '#more'>6. Join More than 2 Tables</a></th>
                <th align=left colspan=2><a href = '#child'>7. Join Child Parent Relationship</a></th>
        </tr>    
</table>

### Tables (Example)

### Employee Table

E_ID | EmployeeName
--- | ---

### Salary Table

E_ID | D_ID |  Salary
--- | --- | ---

### Department Table

D_ID | DepartmentName | Manager
--- | --- | ---

<h3 name='inner'>1. Inner Join</h3>

Join matching `rows` | `records` in both the tables.

```SQL
SELECT Orders.ID, Customers.Name
FROM Orders
INNER JOIN Customers 
ON Orders.ID = Customers.ID;
```

<h3 name='left'>2. LEFT Join</h3>

Join all the rows from `left` table and matching rows from `right` table.

```SQL
SELECT O.ID, C.Name
FROM Orders O
LEFT JOIN Customers C
ON O.ID = C.ID;
```

<h3 name='right'>3. RIGHT Join</h3>

Join all the rows from `right` table and matching rows from the `left` table.

```SQL
SELECT O.ID, C.Name
FROM Orders O
RIGHT JOIN Customers C
ON O.ID = C.ID;
```

<h3 name='self'>4. SELF Join</h3>

Join with Itself.

```SQL
SELECT DISTINCT E.Name
FROM Employees E
INNER JOIN Managers M
ON E.ID = M.ID;
```

<h3 name='outer'>5. OUTER Join</h3>

Join all records from both tables, even if there is no matching row.

```SQL
SELECT DISTINCT E.Name
FROM Employees E
FULL OUTER JOIN Managers M
ON E.ID = M.ID;
```

<h3 name='more'>6. Joins ( More than 2 Tables )</h3>

```SQL
SELECT EmployeeName, DepartmentName, Manager, Salary
FROM Employee E
INNER JOIN Salary S
ON E.E_ID  = S.E_ID
INNER JOIN Department D 
ON D.D_ID = S.D_ID;
```

<h3 name='child'>7. Join using Child Parent Relationship</h3>

```SQL
SELECT EmployeeName, DepartmentName, Manager, Salary
FROM Employee E, Salary S, Department D
WHERE E.E_ID = D.E_ID AND D.D_ID = S.D_ID;
```

### Example

```sql
SELECT 
PositionName, Channel, COUNT(ApplicantID) AS ApplicantCount
FROM Applicants AS App
INNER JOIN Positions AS Po ON App.Position = Po.PositionIndex
INNER JOJN Channels AS Ch ON App.ApplicantID = Ch.ID
GROUP BY 1, 2
HAVING COUNT(ApplicantID) > 4
ORDER BY 1, 3 DESC;
```

```sql
SELECT 
Manager, PositionName, Recruiter, ApplicantName
FROM Applicant AS App
INNER JOIN Positions AS Po ON App.Position = Po.PositionIndex
FULL JOIN Channels AS Ch ON App.ApplicantID = Ch.ID
INNER JOIN Managers AS Mn ON Po.Department = mn.department
ORDER BY 1, 2, 3
```
