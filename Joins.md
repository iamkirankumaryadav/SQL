# JOINS

<table>
        <tr><th>Joins</th><th>Description</th></tr>
        <tr><td><a href = '#inner'>1. Inner Join</a></td><td>Join matching rows in both tables</td></tr>
        <tr><td><a href = '#left'>2. Left Join</a></td><td>Join all the rows from the left and matching rows from the right table</td></tr>
        <tr><td><a href = '#right'>3. Right Join</a></td><td>Join all the rows from the right and matching rows from the left table</td></tr>
        <tr><td><a href = '#self'>4. Self Join</a></td><td>Join by itself (Different columns of same table)</td></tr>
        <tr><td><a href = '#outer'>5. Outer Join</a></td><td>Join all the rows from both tables</td></tr>
        <tr><td><a href = '#more'>6. Join more than 2 tables</a></td><td></td></tr>
        <tr><td><a href = '#child'>7. Join Child Parent Relationship</a></td><td></td></tr>    
</table>

### Tables (Example)

### **Employee Table**

E_ID | EmployeeName
--- | ---

### **Salary Table**

E_ID | D_ID |  Salary
--- | --- | ---

### **Department Table**

D_ID | DepartmentName | Manager
--- | --- | ---

<h3 name='inner'>1. Inner Join</h3>

```SQL
# Join matching rows in both tables:
SELECT orders.ID, customers.Name
FROM orders
INNER JOIN customers 
ON orders.ID = customers.ID;

SELECT * FROM employees e 
INNER JOIN departments d
ON e.department_id = d.department_id
```

<h3 name='left'>2. LEFT Join</h3>

- Join all the rows from the left table and matching rows from the right table.
- If there are no matches in the right table, Null values are returned for the right table columns.

```SQL
SELECT o.ID, c.Name
FROM Orders o
LEFT JOIN Customers c
ON o.ID = c.ID;

SELECT * FROM employees e 
LEFT JOIN departments d
ON e.department_id = d.department_id
```

<h3 name='right'>3. RIGHT Join</h3>

- Join all the rows from the right table and matching rows from the left table.
- If there are no matches in the left table, Null values are returned for the left table columns.

```SQL
SELECT o.ID, c.Name
FROM Orders o
RIGHT JOIN Customers c
ON o.ID = c.ID;

SELECT * FROM employees e 
RIGHT JOIN departments d
ON e.department_id = d.department_id;
```

<h3 name='self'>4. SELF Join</h3>

```SQL
# Join the table with Itself:
SELECT DISTINCT E.Name
FROM Employees E
INNER JOIN Managers M
ON E.ID = M.ID;

SELECT * FROM employees e 
INNER JOIN departments d
ON e.department_id = d.department_id;

SELECT * FROM employees e1, employee e2
WHERE e1.employee_id = e2.employee_id;
```

<h3 name='outer'>5. OUTER Join</h3>

Join all records from both tables, even if there is no matching row.

`Null` values are returned for the columns that do not have a match.

```SQL
SELECT DISTINCT E.Name
FROM Employees E
FULL OUTER JOIN Managers M
ON E.ID = M.ID;

SELECT *
FROM employees e
LEFT JOIN departments d
ON e.employee_id = d.employee_id
UNION
SELECT *
FROM employees
RIGHT JOIN departments
ON e.employee_id = d.employee_id;
```

<h3 name='more'>6. Joins ( More than 2 Tables )</h3>

```SQL
SELECT E.EmployeeName, D.DepartmentName, E.Manager, S.Salary
FROM Employee E
INNER JOIN Salary S
ON E.E_ID  = S.E_ID
INNER JOIN Department D 
ON D.D_ID = S.D_ID;
```

<h3 name='child'>7. Join using Child Parent Relationship</h3>

```SQL
SELECT E.EmployeeName, D.DepartmentName, E.Manager, S.Salary
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
