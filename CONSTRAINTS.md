# `Constraints`

### Constraints adds data validation rules.

- Invalid data won't be allowed in the database.
- User will receive an error message and will need to try again.
- Ensure that stored records meet the table's requirements.

```sql
CREATE TABLE IF NOT EXISTS DatabaseName.SchemaName.TableName(
  ID INT NOT NULL UNIQUE PRIMARY KEY,
)
```

### UNIQUE
- Each value in a column will only appear once, it will not allow to insert duplicate value.

### NULL
- Column will allow NULL values ( Used for optional fields )

### NOT NULL
- Column will not allow NULL values ( Used for mandatory | required field )

### DEFAULT
- Default value will be considered automatically if the person fails to enter.

### CHECK
- Add condition for entering the data value, data is validated before saving.

### PRIMARY KEY (PK)
- Consider the column as a primary key. 

### FOREIGN KEY (FK)
- Consider the column as a foreign key.

### INDEXES
- Keep track of records and help to retrieve the records easily and quickly.
- Added to any columns used in frequent searches or joins.
- Primary keys are created as a clustered index.
- Indexes can also be added to any additional field other than primary key (Non Clustered Index)
- Adding index slow downs the insert operations, after every insert or update the indexes are rebuilt.
