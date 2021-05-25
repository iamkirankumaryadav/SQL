# Pattern Matching

Allows to Search for `Pattern` in Data ( If you don't know the Exact Word or Phrase )

`LIKE` Operator is used in a `WHERE` Clause to Search for a Specified Pattern in a Column.

The Percent Sign ( `%` ) represents Zero, One or Multiple Characters.

The Underscore Sign ( `_` ) represents Single Character.

LIKE Operator |	Description
--- | ---
'a%' |	Finds any values that `start` with "a"
'%a'	| Finds any values that `end` with "a"
'%or%' |	Finds any values that have "or" in `any` position
'\_r%'	| Finds any values that have "r" in the `second` position
'a_%'	| Finds any values that `start` with "a" and are at least 2 characters in length
'a__%' |	Finds any values that `start` with "a" and are at least 3 characters in length
'a%o' | Finds any values that `start` with "a" and `ends` with "o"

```SQL
SELECT Column1, Column2
FROM TableName
WHERE Column1 LIKE 'a%';
```
Symbol | Description |	Example
--- | --- | ---
\* |	Represents `Zero` or `More` Characters | bl* finds bl, black, blue, and blob
\? |	Represents a `Single` Character |	h?t finds hot, hat, and hit
\[] |	Represents any `Single` Character within the brackets |	h\[oa]t finds hot and hat, but not hit
\! |	Represents any character not in the brackets | h\[!oa]t finds hit, but not hot and hat
\-	| Represents a range of characters | c\[a-b]t finds cat and cbt
\#	| Represents any single numeric character |	2#5 finds 205, 215, 225, 235, 245, 255, 265, 275, 285, and 295
