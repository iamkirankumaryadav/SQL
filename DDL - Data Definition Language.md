# **Data Definition Language (DDL)**

- Define, modify, or delete the structure of the database objects (tables, views, indexes).
- All the commands of DDL are auto-committed (Permanently save all the changes in the database)

<a href=#create><strong>CREATE</strong></a> | 
<a href=#alter><strong>ALTER</strong></a> | 
<a href=#drop><strong>DROP</strong></a> | 
<a href=#truncate><strong>TRUNCATE</strong></a> 

<h3 name=create><strong>CREATE</strong></h3>

**Create Schema:**
```sql
-- Syntax:
CREATE SCHEMA IF NOT EXISTS schema_name;

-- Example:
CREATE SCHEMA IF NOT EXISTS employee_schema;
```
**Create database:**
```sql
-- Syntax:
CREATE DATABASE database_name;

-- Example:
CREATE DATABASE employee_details;
```
**Enter into the database:**
```sql
-- Syntax:
USE database_name

-- Example:
USE employee_details;
```
**Create Table:**
```sql
-- Syntax:
CREATE TABLE table_name(
    column1 datatype constraints,
    column2 datatype constraints,
    column3 datatype constraints
);

-- Example:
CREATE TABLE employee(
  employee_id INT IDENTITY PRIMARY KEY,
  first_name VARCHAR(25),
  last_name VARCHAR(25),
  age INT CHECK (Age >= 18) NOT NULL,
  birth_date DATE,
  gender VARCHAR(1),
  designation VARCHAR(25),
  city VARCHAR(25) DEFAULT 'Bengaluru'
)
```
**Create View:**
```sql
CREATE VIEW staff_view AS
SELECT s.ID, s.last_name, cd.company
FROM staff s
LEFT JOIN company_division cd
ON s.department = cd.department;
```
**Create Index:**
```sql
CREATE INDEX idx_staff_last_name
ON staff
USING (last_name);
```

<h3 name=alter><strong>ALTER</strong></h3>

- Alter/Modify/Change table structure (data type, column names, add or drop columns).
- Either to modify the characteristics of an existing attribute or probably to add a new attribute.

**Drop an existing column from the table:**
```sql
-- Syntax:
ALTER TABLE table_name
DROP COLUMN column_name;

-- Example:
ALTER TABLE employee
DROP COLUMN email;
```
**Add a new column in the table:**
```sql
-- Syntax:
ALTER TABLE table_name
ADD column1 datatype constraints, column2 datatype constraints;

-- Example:
ALTER TABLE employee
ADD age INT, department VARCHAR(25);
```
**Modify the data type of an existing column in a table:**
```sql
ALTER TABLE employee
ALTER COLUMN country VARCHAR(25);
```
**Rename the table name:**
```sql    
ALTER TABLE table_name
RENAME TO new_table_name;    
```    
**Rename an existing column name in the table:**
```sql
ALTER TABLE table_name
RENAME COLUMN old_name TO new_name;   
```

<h3 name=drop><strong>DROP</strong></h3>

**Delete the entire table data including the structure, metadata, values and constraints.**
```sql
DROP TABLE employee;
```
    
<h3 name=truncate><strong>TRUNCATE</strong></h3>

**Delete only the data values from the table, while retaining the structure and metadata of the table.**
```sql
TRUNCATE TABLE employee;
```
