# CUBE
Organize **GROUP BY** subsets using all possible combinations.
```SQL
SELECT R.CountryName, R.RegionName, D.DepartmentName, COUNT(E.*) -- Count the total number of employees.
FROM Employee E
JOIN Region R ON E.RegionID = R.ID
JOIN Department D ON E.DepartmentID = D.ID
GROUP BY CUBE(1, 2, 3)
ORDER BY 1, 2, 3
```
