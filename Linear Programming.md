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

1974 Kachian LP can be done in polynomial time called Ellipsoid Algorithm, slow in practice

K1984 karmarkal faster aclled interior poinMoevs inside the poly tops while simplex only moves on outer faces of polytops



A cargo plane can carry a maximum weight of 100 tons and a  
maximum volume of 60 cubic meters. There are three materials to  
be transported, and the cargo company may choose to carry any  
amount of each, up to the maximum available limits given below.  
Write a linear program that optimizes revenue within the  
constraints.  
Density Volume Price  
Material 1 2 tons/m3 40 m3 $1,000 per m3  
Material 2 1 tons/m3 30 m3 $2,000 per m3  
Material 3 3 tons/m3 20 m3 $12,000 per m3
To write a linear program that optimizes revenue within the constraints

Reveju8e is max
Let x1 x2 x3 bhe the volumes

Objective function is to max (1000x1 + 2000x x2 + 12000 x3)

Subject to the following constraints
2x1 + x2 + 3x3 <= 100
x1 + x2 +x3 <= 60

0<= xd1 <= 40, 0<= x2<= 30, 0<= x3<= 30

In matrix form

x1 <=40 -> 1x1 + 0x2 + 3x3 <= 4-
x2<=30-> 0x1 +1x2 +0x3 <= 3-

x = (X1 X2 X3)
C = (1000, 2000, 12000)
b = (100,60,40,30,20)
A = (2 1 3, 1 1 1, 1 0 0, 0 1 0, 0 0 1)


For every linear program there is a dual linear program

Duality
The dual of the standard (primal) maximum problem
max cT x
Ax <= b ad x>0= 0 Is primal


Is defined to tbe the standard minimum problem

min bTy
ATy >= c and y>= 0 dual

Example duality

max(7x1 - x2 + 5x3)  
x1 + x2 + 4x3 ≤ 8  
3x1 - x2 + 2x3 ≤ 3  
2x1 + 5x2 - x3 ≤ -7  
x1, x2 ,x3 ≥ 0

rite the dual problem

Primal LP
max ( cT x)  
A x ≤ b  
x ≥ 0

Dual LP
min ( bT y)  
AT y ≥ c  
y ≥ 0