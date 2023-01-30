## Aggregates

Basic (Self Explanatory):
- Sum
- Avg
- Min
- Max
- Count
Are only applied on Scalar Values except Count.
Only Count can be applied to non Scalar Values

Count: Counts the number of tuples.

## Group By

Follows the Where clause
Without a Group By clause, result is ONE group.
After Groups are formed, ORDER BY and DISTINCT is applied

Example: 
```SELECT studioName, SUM(length) FROM Movies GROUP BY studioName;```
This return one tuple that combines all the different tuples into one based on studioName