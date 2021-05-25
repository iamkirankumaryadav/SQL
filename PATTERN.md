# Pattern Matching

Allows to Search for `Pattern` in Data ( If you don't know the Exact Word or Phrase )

`LIKE` Operator is used in a `WHERE` Clause to Search for a Specified Pattern in a Column.

The Percent Sign ( `%` ) represents Zero, One or Multiple Characters.

The Underscore Sign ( `_` ) represents Single Character.

LIKE Operator |	Description
--- | ---
'a%' |	Finds any values that start with "a"
'%a'	| Finds any values that end with "a"
'%or%' |	Finds any values that have "or" in any position
'\_r%'	| Finds any values that have "r" in the second position
'a_%'	| Finds any values that start with "a" and are at least 2 characters in length
'a__%' |	Finds any values that start with "a" and are at least 3 characters in length
'a%o' | Finds any values that start with "a" and ends with "o"

```SQL
SELECT Column1, Column2
FROM TableName
WHERE Column1 LIKE 'a%';
```
