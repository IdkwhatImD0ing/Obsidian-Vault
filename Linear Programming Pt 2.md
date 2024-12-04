REview
We say that a maximization linear program with n variables is in  
standard form if for every variable xk we have the inequality xk ≥ 0  
and other m linear inequalities:  
max ( cT x )  
subject to  
A x ≤ b  
x ≥ 0  
The LP can be solved in polynomial time for real variables xk.  
In case of integer variables, we do not have a polynomial solver.

Dual LP  
To every linear program there is a dual  
linear program

DualityDuality  
Definition. The dual of the standard (primal) maximum problem  
maxx cTx  
Ax ≤ b and x ≥ 0  
is defined to be the standard minimum problem  
miny bTy  
ATy ≥ c and y ≥ 0
\

So what is Np Compeltness?

In 1900 Hilbert presented a list of 23  
challenging (unsolved) problems in math

n 1935 Alan Turing described a model of  
computation, known today as the Turing  
Machine (TM).  
Alan Turing  
(1936, age 22)  
A problem P is computable (or decidable) if  
it can be solved by a Turing machine that  
halts on every input.

P has an algorithm

Runtime Complexity  
Definition: The running complexity is the function  
f : N → N such that f(n) is the maximum number of  
steps that M uses on any input of length n.  
A problem P is decidable if it can be solved by a Turing machine  
that always halts.

