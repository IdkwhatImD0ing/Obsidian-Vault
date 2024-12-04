Linear programming
Formally, to reduce a problem Y to a problem X  
(we write Y ≤p X) we want a function f that maps  
Y to X such that:  
• f is a polynomial time computable  
• ∀instance y ∈ Y is solvable if and only if f(y) ∈ X is  
solvable.

For example A company wishes to produce two types of souvenirs: type-A  
will result in a profit of $1.00, and type-B in a profit of $1.20.  
To manufacture a type-A souvenir requires 2 minutes on  
machine I and 1 minute on machine II.  
A type-B souvenir requires 1 minute on machine I and 3  
minutes on machine II.  
There are 3 hours available on machine I and 5 hours available  
on machine II.  
How many souvenirs of each type should the company make in  
order to maximize its profit?


let x>= 0 be the number of type a
let y>= 0 be the number of type b
objective function is to find th emax of (x+1.2b) x, y

A linear problem we want to maximumixe the objective function subject to the system of inequalities
2x + y <=180

x + 3y <= 300
x>=0 y>= 0

Need to find the deasible point that is the farthest in the objective direction

f a linear programming problem has a solution, then it must occur  
at a vertex, or corner point, of the feasible set S associated with  
the problem.  
Fundamental Theorem  
If the objective function P is optimized at two adjacent vertices of  
S, then it is optimized at every point on the line segment joining  
these vertices, in which case there are infinitely many solutions to  
the problem.

Existence of solution

supposed we are given a lp problem with a feasible set S and an objective funciton P

there is 3 cases

S is empty, LP has no solution

S is unbounded,  LP may ot may not hav a solution'

S is bounded, lp has a solutoin(s)

Standard LP form

A maximuimiation linear program with n variables in in standard form if for every variable x we have theinequality x>= 0 and for all  other m linear inequalities

A lp in stanfard fprom is written as max(c1x1 + ... +cnxn)

sbuject to azzx1 + ... + a1nxn <= b1

and am1x1 + ... + amnxn <= bm

What does this mean???

Standard LP in Matrix Form  
max ( cT x )  
subject to  
A x ≤ b  
x ≥ 0  
The vector c is the column vector (c1, . . . , cn).  
The vector x is the column vector (x1, . . . , xn).  
The matrix A is the n × m matrix of coefficients of the left-hand  
sides of the inequalities, and  
b= (b1, . . . , bm) is the vector of right-hand sides of the  
inequalities.

Stanford algorithn for solving LPs is the simplex algorithm Dantzig 1947

The algorithm starts by finding a vertex of the polytope and then moving to a neighbor with increased cost as long as this is possible. By linearity and covexityo once it gets stuck it has found the optimal solution

Does not run in polynomial time


