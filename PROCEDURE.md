# PROCEDURE

```sql
-- Syntax:
CREATE OR REPLACE PROCEDURE ProcedureName

@Parameters datatypes(size)

AS

BEGIN

DECLARE @Variables datatypes(size)
-- Create dynamic tables and perform calculations...

EXCEPTION
-- Exception Handling Part


-- SELECT dynamic tables created inside the procedure...
END

-- Execute the procedure by running below line.
-- EXEC ProcedureName Arguments

GO
```
