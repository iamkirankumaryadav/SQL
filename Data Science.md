# SQL for Data Science

### **Data Science operations using SQL**
- Linking data from different data stores ( Data Warehouse, Data Lakes, Databases )
- Filtering, cleaning and reformatting data for different uses ( EDA, Analysis, Dashboards )
- Aggregating data to provide big-picture summaries.
- Answering specific questions about business operations ( Current year profit, Average sale, Trends )

### **Source of Data**
1. Relational and NoSQL (Non Relational) Databases.
2. Data from mobile applications, IoT devices, web logs and automated systems.
3. Manually managed data for training.

### **ETL: Extract Transform Load**
- **Extract:** Read the data from various data sources.
- **Transform:** Clean, preprocess and reshape the data (Trim whitespace, reformat date, standardize value, convert data type)
- **Load:** Write, push or dump into a data warehouse or database.

### **Queries**
<a href='#count'>1. Counting Rows and Items</a>
<a href='#agg'>2. Aggregation Functions</a>
<a href='#ext'>3. Extreme Value Identification</a>
<a href='#slice'>4. Slicing Data</a>
<a href='#sort'>5. Sorting Data</a>
<a href='#filter'>6. Filter Patterns</a>
<a href='#group'>7. Group By Filtering</a>

### **Table**
| **ID** | **first_name** | last_name | age | gender | city | birthday | 
| --- | --- | --- | ---: | :---: | --- | ---: |
| 1 | Kirankumar | Yadav | 25 | M | Thane | 1996-02-07 |
| 2 | Paramveer | Yadav | 26 | M | Kalyan | 1995-01-21 |
| 3 | Gaurav | Sonar | 26 | M | Kalyan | 1995-03-21 |
| 4 | Pranit | Sorte | 28 | M | Ambernath | 1993-06-21 |

### **Create Table**
``` SQL
CREATE TABLE Employee(
ID INT IDENTITY,
first_name VARCHAR(25) NOT NULL,
last_name VARCHAR(25),
age INT CHECK (Age>=18),
gender VARCHAR(1),
city VARCHAR(25) 
)
```

### **INSERT: Insert Rows**
``` SQL
INSERT INTO employee(first_name, last_name, age, gender, city)
VALUES('Kirankumar', 'Yadav', 25, 'M', 'Thane')
```

### **ALTER: Add New Column to Table: DATE (YYYY-MM-DD)**
``` SQL
ALTER TABLE employee
ADD birthday DATE 
```

### **UPDATE: Update Table Value**
``` SQL
UPDATE employee
SET birthday='1996-02-07' WHERE ID=1
```

### **SELECT**
``` SQL
SELECT * FROM employee 
```

### **INSERT: Insert Multiple Rows**
``` SQL
INSERT INTO employee(first_name, last_name, age, gender, birthday)
VALUES('Paramveer', 'Yadav', 28, 'M', 'Kalyan', '1995-01-21'),
      ('Gaurav', 'Sonar', 28, 'M', 'Kalyan', '1995-03-21'),
      ('Pranit', 'Sorte', 30, 'M', 'Ambernath', '1993-06-21')
```

### **DELETE**
``` SQL
DELETE FROM employee
WHERE ID=5
```
                      
### **DISTINCT: Unique Values in a Column**
``` SQL
SELECT DISTINCT(age)
FROM employee
```
<h3 name='count'>COUNT: Number of Rows or Items </h3>

``` SQL
SELECT COUNT(ID)
FROM employee
```

<h2 name='agg'>Aggregate Functions</h2>

#### **SUM and AVG: Sum and Average of Numerical Values**
``` SQL
SELECT
SUM(age) AS total_age,
AVG(age) AS average_age
FROM employee
```

<h2 name='ext'>Extreme Value Identification</h2>

#### **MAX and MIN: Maximum and Minimum Numeric Value**
``` SQL
SELECT
MAX(Age) AS max_age,
MIN(Age) AS min_age
FROM employee
```

<h2 name='slice'>Slicing Data</h2>

``` SQL
SELECT * FROM employee
WHERE city='Kalyan'
```

<h2 name='sort'>Sorting Data</h2>

``` SQL
SELECT * FROM employee
ORDER BY age DESC

SELECT * FROM employee
ORDER BY first_name -- Alphabetical Order
```

<h2 name='filter'>Filter Patterns</h2>

``` SQL
SELECT * FROM employee
WHERE first_name LIKE 'K%' -- Starting with K

SELECT * FROM employee
WHERE first_name LIKE '%R' -- Ending with R

SELECT * FROM employee
WHERE first_name LIKE '%an%' -- Contains an
```

<h2 name='group'>Group By Filtering (Aggregation + Having)</h2>

``` SQL
SELECT SUM(age) AS age, city 
FROM employee 
GROUP BY city

SELECT SUM(age) AS age, last_name 
FROM employee 
GROUP BY last_name
```

``` SQL
SELECT SUM(age) AS age, city 
FROM employee 
GROUP BY city 
HAVING SUM(age) > 30
```

### **OFFSET**
``` SQL
SELECT first_name, last_name
FROM employee
ORDER BY city
OFFSET 2 ROWS
```

### **TOP** 
``` SQL
SELECT TOP 2 *
FROM employee
```

### **BETWEEN**
``` SQL
SELECT * FROM employee
WHERE age BETWEEN 26 AND 28
```

### **IN**
``` SQL
SELECT * FROM employee
WHERE age IN (26,28)
```

### **IS NOT NULL**
``` SQL
SELECT * FROM employee
WHERE age IS NOT NULL
```

### **DROP Table**
```SQL
DROP TABLE employee
```
