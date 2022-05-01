# Concepts

### Changing Schema

1. Adding columns in an existing table.
2. Removing columns from an existing table.
3. Adding or changing constraints of an existing table.
4. Changing data type.

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
```   
Output
First_Name| Last_Name | Designation | Department
:--- | :--- | :--- | :---
Kirankumar | Yadav | Data Scientist | Data Science
Suraj | MS | MLE | Data Science
Pavan | Kumar | Statistician | Data Science

