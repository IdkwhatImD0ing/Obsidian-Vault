## Join On
Combines two tables based on a shared piece of information
```
R JOIN S ON r.a = s.b is the same as

SELECT * from R, S WHERE r.a=r.b
```
## Cross Join
```R CROSS JOIN S;```
Same as
```SELECT * from R, S;```
Returns the cartesian product

## Natural Join

```R NATURAL JOIN S;```
R(A,B,C) and S(C,D,E)

would result in (A,B,C,D,E)


