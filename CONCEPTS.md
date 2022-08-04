# Fundamental Concepts

- `SQL` is as a standardized structured query language that helps to communicate with `RDBMS`
- `Database` is an actual set of data while `DBMS` is software that helps you manage information in database.
- `DBMS` simplifies your `data collection`, `maintenance`, `storage` and `tracking`
- `DBMS` helps organize and maintain your data.
- `SQL` helps to define tables using columns and rows to find and update the values in specific cells.
- `Columns`in relational database tables must have a unique name and homogeneous values.
- `Row` is a single record of data.
- `NULL` value stands for a blank field (Not zero and no whitespace)

1. <a href=#create>Creating a table</a>
2. <a href=#insert>Inserting rows</a>
3. <a href=#drow>Deleting rows</a>
4. <a href=#delete>Deleting a table</a>
5. <a href=#drop>Drop existing table</a>
6. <a href=#schema>Changing Schema</a>
7. <a href=#id>ID Column</a>
8. <a href=#null>NULL value</a>
9. <a href=#order>Ordering rows</a>

<h2 name=create>Creating a table</h2>

```sql
CREATE TABLE Employee
(
  ID INTEGER PRIMARY KEY,
  First_Name TEXT,
  Last_Name TEXT,
  Designation TEXT
);
```

<h2 name=insert>Inserting rows</h2>

```sql
# Insert every row values :
INSERT INTO Employee
VALUES ('Kirankumar', 'Yadav', 'Data Scientist');

# Insert only specific row values, rest will be NULL :
INSERT INTO Employee (First_Name, Last_Name)
VALUES ('Kisankumar', 'Yadav')

# Insert a new row with NULL values :
INSERT INTO Employee DEFAULT VALUES;

# Insert a new row values from an existing table :
INSERT INTO Employee (First_Name, Last_Name, Designation)
SELECT First, Last, Role FROM Training;
```

<h2 name=drow>Deleting rows</h2>

```sql
DELETE FROM Employee WHERE ID = 3
```

<h2 name=delete>Deleting a table</h2>
```sql
DROP TABLE Employee
```

<h2 name=drop>Deleting existing table</h2>

- Drop the table only if that table exists in a database.
- No Error will be visible if there is no such table in the database.
- Normally if we just drop the table it will display an error that there is no such table in the database.

```sql
DROP TABLE IF EXISTS Employee;
```

<h2 name='schema'>Changing Schema</h2>

1. **Adding** columns in an existing table.
2. **Removing** columns from an existing table.
3. Adding or changing **constraints** of an existing table.
4. Changing **data type** of an existing column.

```sql
CREATE TABLE Employee
(
  First_Name TEXT,
  Last_Name TEXT,
  Designation TEXT
);

INSERT INTO Test
VALUES ('Kirankumar', 'Yadav', 'Data Scientist'),
VALUES ('Suraj', 'MS', 'MLE'),
VALUES ('Pavan', 'Kumar', 'Statistician');

SELECT * FROM Employee;
```
Output
First_Name| Last_Name | Designation
:--- | :--- | :--- 
Kirankumar | Yadav | Data Scientist
Suraj | MS | MLE  
Pavan | Kumar | Stistician

```sql
ALTER TABLE 
ADD Department TEXT DEFAULT 'Data Science';

SELECT * FROM Employee;
```   
Output
First_Name| Last_Name | Designation | Department
:--- | :--- | :--- | :---
Kirankumar | Yadav | Data Scientist | Data Science
Suraj | MS | MLE | Data Science
Pavan | Kumar | Statistician | Data Science

---

<h2 name='id'>ID Column</h2>

1. Column that holds a **unique** value for each row in a table.
2. Typically ID columns are **automatically** populated or incrmented.

```sql
CREATE TABLE Employee
(
  Employee_ID INTEGER PRIMARY KEY
  First_Name TEXT,
  Last_Name TEXT,
  Designation TEXT
);

INSERT INTO Test ( First_Name, Last_Name, Designation )
VALUES ('Kirankumar', 'Yadav', 'Data Scientist'),
VALUES ('Suraj', 'MS', 'MLE'),
VALUES ('Pavan', 'Kumar', 'Statistician');

SELECT * FROM Employee;
```
Output
Employee_ID | First_Name| Last_Name | Designation
:--- |:--- | :--- | :--- 
1 | Kirankumar | Yadav | Data Scientist
2 | Suraj | MS | MLE  
3 | Pavan | Kumar | Stistician
---

<h2 name=null>NULL value</h2>

```sql
# Fetch only rows with NULL value :
SELECT * FROM Employee
WHERE Designation IS NULL

# Fetch only NON NULL rows :
SELECT * FROM Employee
WHERE Designation IS NOT NULL
```

<h2 name=order>Ordering rows</h2>

```sql
# Order the rows in Ascending Order | ASC by default :
SELECT First_Name, Last_Name, Designation 
FROM Employee
ORDER BY First_Name;

# Order the rows in Descending Order :
SELECT First_Name, Last_Name, Designation 
FROM Employee
ORDER BY First_Name DESC;

# Order the rows based on multiple columns :
SELECT First_Name, Last_Name, Designation 
FROM Employee
ORDER BY First_Name ASC, Last_Name ASC, Designation DESC;
```
