# `String` Functions and Operations

### Create BOOLEAN Result

```sql
SELECT 
Name, Age, Designation, (Designation LIKE 'Data Scientist') AS DataScience
FROM Employee;
```

Name | Age | Designation | DataScience
:--- | :--- | :--- | :---
Kirankumar Yadav | 26 | Data Scientist | true
Paramveer Yadav | 27 | Data Analyst | false
Suraj MS | 27 | Data Scientist | true
Gaurav Sonar | 28 | Angular Developer | false
Pranit Sorte | 29 | Program Manager | false

### `SUBSTRING`

```sql
SELECT SUBSTRING('Kirankumar Yadav', 1, 10) AS Name;
```

Name
:---
Kirankumar

### `CONCAT`

```sql
SELECT CONCAT(FirstName, ' ', LastName) AS Name;
```

Name
:---
Kirankumar Yadav

### `UPPER`

```sql
SELECT UPPER('Kirankumar Yadav') AS Name;
```

Name
:---
KIRANKUMAR YADAV


### `LOWER`

```sql
SELECT LOWER('Kirankumar Yadav') AS Name;
```

Name
:---
kirankumar yadav

`TRIM`

```sql
SELECT "  Kirankumar Yadav  " AS Name;
```

Name
:---
Kirankumar Yadav
