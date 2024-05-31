# **Data Manipulation Language (DML)**

- SQL commands designed to interact with the data stored within database tables.
- The command is not auto-committed (It can't permanently save all the changes in the database) they can be rollbacked.

<a href=#select><strong>SELECT</strong></a> | 
<a href=#insert><strong>INSERT</strong></a> | 
<a href=#update><strong>UPDATE</strong></a> | 
<a href=#delete><strong>DELETE</strong></a> 

<h3 name=select><strong>SELECT</strong></h3>

```sql
# Select all the columns:
SELECT *
FROM Employee;
```            

```sql
# Select specific columns:
SELECT first_name, last_name
FROM Employee;
```

<h3 name=insert><strong>INSERT</strong></h3>

```sql
# Insert single row:
INSERT INTO Employee(FirstName, LastName, Email)  
VALUES('Kirankumar', 'Yadav', 'Kirankumaryadav@gmail.com');
```

```sql
# Insert multiple rows:
INSERT INTO Employee(FirstName, LastName, Email)  
VALUES('Kirankumar', 'Yadav', 'Kirankumar.Yadav@gmail.com'),
      ('Kisankumar', 'Yadav', 'Kisankumar.Yadav@gmail.com'),
      ('Rohit', 'Yadav', 'Rohit.Yadav@gmail.com'),
      ('Arpit', 'Yadav', 'Arpit.Yadav@gmail.com');
```

<h3 name='update'><strong>UPDATE</strong></h3>
      
```sql
# Update the value of a column in a table:
UPDATE Employee
SET Designation = 'Data Scientist'
WHERE FirstName = 'Kirankumar' 
AND LastName = 'Yadav' 
AND DateOfBirth = '07/02/1996';
```

<h3 name=delete><strong>DELETE</strong></h3>

```sql
# Remove one or more rows from a table:
DELETE 
FROM Supplier
WHERE SupplierID = 2;
# WHERE Clause is only used with DELETE command (Not with DROP and TRUNCATE commands)
```
