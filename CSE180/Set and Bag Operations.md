## Set Union
Keyword: Union (Set), Union (Bag)

### Input to union 
Must have the same attributes, same types, and same order

### Output of union
Same Schema as either

### Meaning
Set of all tuples from Q1 and from Q2. Built in Distinct Keyword

```(SELECT * from Q1) UNION (SELECT * from Q2)```

## Intersection
Keyword: INTERSECT (Set), INTERSECT ALL (Bag)

### Input to intersection
Must have the same attributes, types, and order

### Output
Same Schema

### Meaning
Distinct elements in both Q1 and Q2

## Difference
Keyword: EXCEPT (Set), EXCEPT ALL (Bag)

### Input to difference
Must have the same attributes, types, and order

### Output
Same Schema

### Meaning
Distinct elements that are in Q1 but not in Q2
