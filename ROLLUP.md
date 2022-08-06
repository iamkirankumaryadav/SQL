# `ROLLUP`

```sql
SELECT
C.StateName
C.CityName
COUNT(S.*) AS TotalCars(M)  -- Count total cars in the state.
FROM State S
JOIN City C
ON S.CityID = C.ID
GROUP BY ROLLUP(C.StateName, C.CityName)
ORDER BY C.StateName, C.CityName;
```

StateName | CityName | TotalCars(M)
:--- | :--- | :---
MH | Mumbai | 250
MH | Pune | 270
MH | Nashik | 199
MH | NULL | 719
GJ | Ahmedabad | 210
GJ | Vadodara | 100
GJ | Kutch | 80
GJ | NULL | 390
NULL | NUL | 1109
