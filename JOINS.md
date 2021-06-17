# JOINS

<table>
        <tr>
                <th align=left><a href = '#inner'>1. Inner Join</a></th>
                <th align=left><a href = '#left'>2. Left Join</a></th>
                <th align=left><a href = '#right'>3. Right Join</a></th>
                <th align=left><a href = '#self'>4. Self Join</a></th>
        </tr>
        <tr>
                <th align=left colspan=2><a href = '#more'>5. Join More than 2 Tables</a></th>
                <th align=left colspan=2><a href = '#child'>6. Join Child Parent Relationship</a></th>
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

Join Matching `Rows` in both the Tables.

```SQL
SELECT Orders.ID, Customers.Name
FROM Orders
INNER JOIN Customers 
ON Orders.ID = Customers.ID;
```

<h3 name='left'>2. LEFT Join</h3>

Join all the Rows from Left Table and Matching Rows from Right Table.

```SQL
SELECT O.ID, C.Name
FROM Orders O
LEFT JOIN Customers C
ON O.ID = C.ID;
```

<h3 name='right'>3. RIGHT Join</h3>

Join all the Rows from Right Table and Matching Rows from the Left Table.

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

<h3 name='more'>5. Joins ( More than 2 Tables )</h3>

```SQL
SELECT EmployeeName, DepartmentName, Manager, Salary
FROM Employee E
INNER JOIN Salary S
ON E.E_ID  = S.E_ID
INNER JOIN Department D 
ON D.D_ID = S.D_ID;
```

<h3 name='child'>6. Join using Child Parent Relationship</h3>

```SQL
SELECT EmployeeName, DepartmentName, Manager, Salary
FROM Employee E, Salary S, Department D
WHERE E.E_ID = D.E_ID AND D.D_ID = S.D_ID;
```
