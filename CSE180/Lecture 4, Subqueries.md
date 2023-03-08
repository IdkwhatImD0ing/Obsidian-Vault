## In

Can do something like where # in (Select * ....)
This finds all the tuples where the value is in the result of a select query

IN is equal to = ANY ([[Important Details#Some / Any|Details]])
Finds one inside multiset

NOT IN is equal to != ALL ([[Important Details#All|Details]])
Finds no matching value inside multiset

!= Any
Not matching one of the values inside the multiset

## From

Can also do something like Select * from Movies,  (Select * ...)
This only searches in the result of the Select query and Movies table.

## Exists

Returns true if there is a record that exists in a table. Basically checks if the result is empty or not.

```Exists Q```
Returns true if Q is a non-empty collection
```x in Q```
Returns true if Q is a non-empty collection and x is in Q

## Any [[Important Details]]

Matches one or more tuples in a table

## All [[Important Details]]

Matches all tuples in a table

## Subqueries inside Subqueries?

When does it end? 
```Select * from (Select * from (Select * from .....))```
This is legal query

## Inner Subqueries can Rely on Outside Queries

Called a Correlation
Select *  FROM Movies m where m.movieYear < ANY (Select ... where m2.movieTitle = m.movieTitle)

Correlation via tuple variable m


