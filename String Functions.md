# **String Functions + Operations**

### **Create BOOLEAN Result**

```sql
SELECT Name, Age, Designation, (Designation LIKE 'Data Scientist') AS DataScience
FROM Employee;
```

Name | Age | Designation | DataScience
:--- | :--- | :--- | :---
Kirankumar Yadav | 26 | Data Scientist | true
Paramveer Yadav | 27 | Data Analyst | false
Suraj MS | 27 | Data Scientist | true
Gaurav Sonar | 28 | Angular Developer | false
Pranit Sorte | 29 | Program Manager | false

### **Extract SUBSTRING from a string**

```sql
SELECT SUBSTRING('Kirankumar Yadav', 1, 10) AS First_Name;
```

First_Name
:---
Kirankumar

### **LIKE: Extract string using Patterns**

- **"_":** represents a single character
- **"%":** represents wild character

```sql
SELECT 
Name, Age, Designation 
FROM Employee
WHERE Designation LIKE '%Developer' -- Ends with Developer LIKE (Software Developer, Hardware Developer...)

...
WHERE Designation LIKE 'Data%' -- Starts with Data LIKE (Data Scientist, Data Analyst, Data Engineer...)

...
WHERE Designation LIKE 'Data%|%Developer' -- Starts with Data or Ends with Developer.
```

### **Concat multiple strings**

```sql
SELECT CONCAT(FirstName, ' ', LastName) AS Name;
```

```sql
-- Using pipe operator:
SELECT 'Kirankumar' || 'Yadav' AS Name;
SELECT first_name || last_name AS Name;
```

Name
:---
Kirankumar Yadav

### **UPPER | LOWER | INITCAP**

```sql
SELECT 
UPPER('Kirankumar Yadav') AS UpperCaseName,
LOWER('Kirankumar Yadav') AS LowerCaseName,
INITCAP('kirankumar yadav') AS TitleCaseName;
```

UpperCaseName | LowerCaseName | TitleCaseName
:--- | :--- | :---
KIRANKUMAR YADAV | kirankumar yadav | Kirankumar Yadav

### **TRIM**

```sql
SELECT "  Kirankumar Yadav  " AS Name;
```

Name
:---
Kirankumar Yadav

### **Select DISTINCT values from column**

```sql
SELECT 
DISTINCT(Designation)
FROM Employee;
```

### **Extension**

```sql
CREATE EXTENSION IF NOT EXISTS fuzzystrmatch
```

### **SOUNDEX:** Finding similar sounding words.

```sql
SELECT 
SOUNDEX('Postgres') = SOUNDEX('Postgress') AS Soundex
```

Soundex
:---
true


```sql
SELECT 
LEVENSHTEIN('Kiran', 'Kisan') AS LS
```

LS
:---
1

```sql
SELECT LEVENSHTEIN('Happy', 'Unhappy') AS LS
```

LS
:---
2
