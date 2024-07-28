# **Data Definition Language (DDL)**

- Define, modify, or delete the structure of the database objects (tables, views, indexes).
- All the commands of DDL are auto-committed (Permanently save all the changes in the database)

<a href=#create><strong>CREATE</strong></a> | 
<a href=#alter><strong>ALTER</strong></a> | 
<a href=#drop><strong>DROP</strong></a> | 
<a href=#truncate><strong>TRUNCATE</strong></a> 

<h3 name=create><strong>CREATE</strong></h3>

```sql
-- Create Schema:
CREATE SCHEMA IF NOT EXISTS schema_name;
```

```sql
-- Create database:
CREATE DATABASE employee_details;
```

```sql
-- Enter into the database:
-- USE database_name

USE employee_details;
```

```sql
-- Create Table:
CREATE TABLE employee(
    employee_ID INT NOT NULL IDENTITY(1, 1) PRIMARY KEY, -- IDENTITY(1,1) Start from 1 and increment by 1.
    first_name VARCHAR(25),
    last_name VARCHAR(25),
    email VARCHAR(25)
);
```

```sql
# Create View:
CREATE VIEW staff_view AS
SELECT s.ID, s.last_name, cd.company
FROM staff s
LEFT JOIN company_division cd
ON s.department = cd.department;
```

```sql
# Create Index:
CREATE INDEX idx_staff_last_name
ON staff
USING (last_name);
```

<h3 name=alter><strong>ALTER</strong></h3>

- Alter/Modify/Change table structure (data type, column names, add or drop columns).
- Either to modify the characteristics of an existing attribute or probably to add a new attribute.

```sql
-- Drop an existing column from the table:
ALTER TABLE employee
DROP COLUMN email;
```

```sql
-- Add a new column in the table:
ALTER TABLE employee
ADD age INT, department VARCHAR(25);
```

```sql
# Modify the size and data type of an existing column in a table:
ALTER TABLE employee
ALTER COLUMN country VARCHAR(25);
```

```sql
-- Rename the table name:    
ALTER TABLE table_name
RENAME TO new_table_name;    
```    

```sql
-- Rename an existing column name in the table:
ALTER TABLE table_name
RENAME COLUMN old_name TO new_name;   
```

<h3 name=drop><strong>DROP</strong></h3>

```sql
-- Delete the entire table data including the structure, metadata, values and constraints.
DROP TABLE employee;
```
    
<h3 name=truncate><strong>TRUNCATE</strong></h3>

```sql
-- Delete only the data values from the table, while retaining the structure and metadata of the table.
TRUNCATE TABLE employee;
```
