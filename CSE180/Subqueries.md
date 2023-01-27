## In

Can do something like where # in (Select * ....)
This finds all the tuples where the value is in the result of a select query

## From

Can also do something like Select * from Movies,  (Select * ...)
This only searches in the result of the Select query and Movies table.

## Subqueries inside Subqueries?

When does it end? 
```Select * from (Select * from (Select * from .....))```
This is legal query

## Inner Subqueries can Rely on Outside Queries

Called a correlation
Select *  FROM Movies m where m.movieYear < ANY (Select ... where m2.movieTitle = m.movieTitle)

