# `DQL` : Data Query Language

### `Create` and `Read` a table with data 

```sql
CREATE Table Employee
(
    Employee_ID INT NOT NULL IDENTITY(1,1) PRIMARY KEY,  # IDENTITY(1,1) Start from 1 and Increment by 1 
    First_Name  NVARCHAR(60),
    Last_Name   NVARCHAR(60),
    Email       NVARCHAR(60)
)
```
