# **Data Manipulation Language (DML)**

- SQL commands designed to interact with the data stored within database tables.
- The command is not auto-committed (It can't permanently save all the changes in the database) they can be rollbacked.

<a href=#select><strong>SELECT</strong></a> | 
<a href=#insert><strong>INSERT</strong></a> | 
<a href=#update><strong>UPDATE</strong></a> | 
<a href=#delete><strong>DELETE</strong></a> 

<h3 name=select><strong>SELECT</strong></h3>

```sql
-- Select all the columns:
SELECT *
FROM employee;
```            

```sql
-- Select specific columns:
SELECT first_name, last_name
FROM employee;
```

<h3 name=insert><strong>INSERT</strong></h3>

```sql
-- Insert single row:
INSERT INTO employee(first_name, last_name, email)  
VALUES('Kirankumar', 'Yadav', 'kirankumar.yadav@gmail.com');
```

```sql
-- Insert multiple rows:
INSERT INTO employee(first_name, last_name, email)  
VALUES('Kirankumar', 'Yadav', 'kirankumar.yadav@gmail.com'),
      ('Kisankumar', 'Yadav', 'kisankumar.yadav@gmail.com'),
      ('Rohit', 'Yadav', 'rohit.yadav@gmail.com'),
      ('Arpit', 'Yadav', 'arpit.yadav@gmail.com');
```

<h3 name='update'><strong>UPDATE</strong></h3>
      
```sql
-- Update the value of a column in a table:
UPDATE employee
SET designation = 'Data Scientist'
WHERE first_name = 'Kirankumar' 
AND last_name = 'Yadav' 
AND birth_date = '1996-02-07';
```

<h3 name=delete><strong>DELETE</strong></h3>

```sql
-- Remove one or more rows from a table:
DELETE 
FROM supplier
WHERE supplier_ID = 2;
-- WHERE Clause is only used with DELETE command (Not with DROP and TRUNCATE commands)
```
