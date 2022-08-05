# `Schema`

- Logical view of entire database, helps to organize objects in a database.
- Defines how the database is organized and how the relation among them are associated.
- Defines the entities and relationship among them.
- Contains descriptive detail about database.
- e.g. There are different departents in any company (IT, Tax, Payroll, HR, Marketing, Sales)
- We can create a seperate schema for each departments in order to organize there data in a logical way.

```sql
-- Creating a database by KTECH company name:
CREATE DATABASE KTECH;

-- Create Schemas for each Department:
USE DATABASE KTECH;
CREATE SCHEMA IF NOT EXISTS IT; -- All IT related data will be stored in IT Schema.
CREATE SCHEMA IF NOT EXISTS HR; -- All HR related data will be stored in HR Schema.
CREATE SCHEMA IF NOT EXISTS Marketing; -- All Marketing related data will be stored in Marketing Schema.

-- Access each schema for creating tables:
CREATE TABLE IF NOT EXISTS KTECH.IT.Employee (ID INT...);
CREATE TABLE IF NOT EXISTS KTECH.HR.Employee (ID INT...);
CREATE TABLE IF NOT EXISTS KTECH.Marketing.Employee (ID INT...);
```

Each database vendors have there own way of representing schemas.

### `Collection` of database objects:

1. Tables (Store Data)
2. Views (Snapshot of a table)
3. Fields
4. Relationships
5. Packages
6. Procedures 
7. Functions
8. Indexes
9. Triggers
10. Directories

```sql
-- User can view all the databases and schemas together:
SHOW DATABASES
```

