# FUNCTION

Similar to `PROCEDURE` except it returns a value.

```sql
-- Syntax
CREATE OR REPLACE FUNCTION FunctionName (Parameter IN VARCHAR)
RETURNS VARCHAR 
AS
BEGIN
-- Calculations part...
RETURN value;
END;
```
