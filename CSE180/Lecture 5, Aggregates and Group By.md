## Aggregates

Basic (Self Explanatory):
- Sum [[Important Details#Sum|Details]]
- Avg
- Min
- Max
- Count [[Important Details#^4c59eb|Details]]
Are only applied on Scalar Values except Count.
Only Count can be applied to non Scalar Values

Count: Counts the number of tuples.

Nulls Are Ignored in all Aggregates EXCEPT Count * 
COUNT * also counts the number of Nulls that appear

[[Important Details#^e5486f|Cannot appear in Where]]

## Group By

Follows the Where clause
Without a Group By clause, result is ONE group.
After Groups are formed, ORDER BY and DISTINCT is applied

Example: 
```SELECT studioName, SUM(length) FROM Movies GROUP BY studioName;```
This return one tuple that combines all the different tuples into one based on studioName

Group By _DOES NOT_ ignore Null. There will a group called Null


## Having

Appears after a Group By

Only adds the Group to the Solution if it meets the conditions