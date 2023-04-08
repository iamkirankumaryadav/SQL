# `DML` : **Data Manipulation Language**

`Modify` the databases. It is responsible for all form of changes in the database.

The command is not auto commited (It can't permanently save all the changes in the database) they can be `rollback`

<a href=#insert><code>INSERT</code></a> <a href=#update><code>UPDATE</code></a> <a href=#delete><code>DELETE</code></a> 

<h2 name=insert color=green><code>INSERT</code></h2>

`Insert` data into the row of a table.

`Single` row:

```sql
-- Insert single row:
INSERT INTO Employee(FirstName, LastName, Email)  
VALUES('Kirankumar', 'Yadav', 'Kirankumaryadav@gmail.com');

-- Insert multiple rows:
INSERT INTO Employee(FirstName, LastName, Email)  
VALUES('Kirankumar', 'Yadav', 'Kirankumar.Yadav@gmail.com'),
      ('Kisankumar', 'Yadav', 'Kisankumar.Yadav@gmail.com'),
      ('Rohit', 'Yadav', 'Rohit.Yadav@gmail.com'),
      ('Arpit', 'Yadav', 'Arpit.Yadav@gmail.com');
```

<h2 name='update'><code>UPDATE</code></h2>
      
`Update` or `modify` the value of a column in a table.      
      
```sql
UPDATE Employee
SET Designation = 'Data Scientist'
WHERE FirstName = 'Kirankumar' 
AND LastName = 'Yadav' 
AND DateOfBirth = '07/02/1996';
```

<h2 name=delete><code>DELETE</code></h2>
      
`Remove` one or more row from a table.

```sql
DELETE 
FROM Supplier
WHERE SupplierID = 2;
-- WHERE Clause is only used with DELETE command (Not with DROP and TRUNCATE commands)
```
