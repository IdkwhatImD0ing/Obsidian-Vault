## Update Anomaly

Employees with the same rank has the same salary scale
Update Anomaly:
 - If one copy of salary scale is changed, then all copies of that salary scale (of the same rank) have to be changed

## Insertion Anomaly

Hiring someone who's rank is 4, their salary sale will be set automatically.
Same with other ranks. But only with prior rank

## Deletion Anomaly

If we delete someone with the rank, how do we store his salary scale?

# Good Schema Design

 - Salary Scale only dependent on Rank
 - No need to depend on other information

### Functional Dependency (FD)
- Getting rid of the anomaly
- One thing determines another
- Basically an implies
- Can't be two different tuples in the table that agree on the left hand side and disagree on the right hand side
- X->Y
	- If the x values are the same, then the y values will be the same
- An FD is a statement about all possible legal instances of a schema. We cannot just look at an instance (or even at a set of instances) to determine which FDs hold