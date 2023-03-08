## Update Anomaly

Employees with the same rank has the same salary scale
Update Anomaly:
 - If one copy of salary scale is changed, then all copies of that salary scale (of the same rank) have to be changed

## Insertion Anomaly

Hiring someone who's rank is 4, their salary sale will be set automatically.
Same with other ranks. But only with prior rank

## Deletion Anomaly

If we delete someone with the rank, how do we store his salary scale?

### Good Schema Design

 - Salary Scale only dependent on Rank
 - No need to depend on other information

# Functional Dependency (FD)
- Getting rid of the anomaly
- One thing determines another
- Basically an implies
- Can't be two different tuples in the table that agree on the left hand side and disagree on the right hand side
- X->Y
	- If the x values are the same, then the y values will be the same
- An FD is a statement about all possible legal instances of a schema. We cannot just look at an instance (or even at a set of instances) to determine which FDs hold

## Armstrong's Axioms

Let X, Y, Z denote sets of attributes over a relational schema R

- ### Reflexivity
	- If Y ⊆ X, then X → Y. ssn, name → name 
		- FDs in this category are called trivial FDs.
- ### Augmentation
	- If X → Y, then XZ → YZ for any set Z of attributes. ssn, name, addr → name addr
- ### Transitivity
	- If X → Y and Y → Z, then X → Z.
	- If ssn → rank, and rank → sal_scale, then ssn → sal_scale

## Union and Decomposition Rules

- ### Union
	- If X → Y and X → Z, then X → YZ.
- ### Decomposition
	- If X → YZ, then X → Y and X → Z

Can be derived using ArmStrong's Axiom

## Boyce-Codd Normal Form

Definition: 
- Let R be a relation schema, F be a set of FDs that holds for R, with A as an attribute in R, and X as a subset of the attributes in R.
- R is in Boyce-Codd Normal Form (BCNF) if:
	- For every FD X → A in F, at least one of following is true: 
		- X → A is a trivial FD (i.e., A ∈ X) 
		- X is a superkey for R.

Desirable for avoiding redundancy


## Third Normal Form

Additional condition for BCNF
```
A is a Prime Attribute. That is, A is part of some key of R.
```
