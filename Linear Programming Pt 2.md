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

What is polynimail time?

A fundamental complexity of class p or PTime is a class of decision problems that can be solved by a determinsitic Turing machine in polynomial time


Fundamental complexity class EXPTIME is a class of decision problems that can be solved by a deterministic Turning in O(2^pn time where pn is a polynial)

Important what is the halting problem?
The problem of deciding whether a given Turning Machine halts when prsented with a given input????
The halting problem is not decidable

Why is it so importnat?
Lots of practical problems are the halting problem in disguise


The deterministic Turing machine means that there is only one valid  
computation starting from any given input. A computation path is like  
a linked list.  
Nondeterministic Turing machine (NDTM) defined in the same way  
as deterministic, except that a computation is like a tree, where at  
any state, it’s allowed to have a number of choices.  
One way to visualize NDTM is that it makes  
an exact copy of itself for each available  
transition, and each machine continues the  
computation.

Now what is NP?
Its a complexity class that can be soled by a nondeterminsitc Turning maching in poolynomial time

NP problem has a certificate that can be checked by a polynomial time deterministic Turning machine
UIse last definiton for proving NP compelteness





It has been proven that Nondeterministic TM can be simulated by  
Deterministic TM. Rabin & Scott in 1959 shown that adding non-  
determinism does not result in more powerful machine.  
But how fast we can do that simulation?  
The famous P ≠ NP conjecture, would answer that we cannot hope to  
simulate nondeterministic Turing machines very fast (in polynomial time).


P and NP complexity classes  
P = set of problems that can be solved in polynomial time by a  
deterministic TM.  
NP = set of problems for which solution can be verified in  
polynomial time by a deterministic TM.

To reduce a decision problem Y to a decision problem X (we write Y ≤p X)  
we want a function f that maps Y to X such that:  
1) f is a polynomial time computable  
2) ∀y ∈ Y (y is instance of Y) is YES if and only if f(y) ∈ X is YES.  
We use this to prove NP completeness:  
knowing that Y is hard, we prove that X is at least as hard as Y.

If we can solve X in polynomial time,  
we can solve Y in polynomial time.

Bipartite Matching ≤p Max-Flow  
Examples:  
If we can solve X in polynomial time,  
we can solve Y in polynomial time.  
Circulation ≤p Max-Flow


If we can solve X, we can solve Y.  
Knowing that Y is hard, we prove that X is harder.  
The contrapositive of the statement "if A, then B"  
is "if not B, then not A."  
If we cannot solve Y, we cannot solve X.  
In plain form: X is at least as hard as Y.

Two ways of using Y ≤p X  
1) Knowing that X is easy  
If we can solve X in polynomial time,  
we can solve Y in polynomial time.  
2) Knowing that Y is hard  
Then we can prove that X is at least as hard as Y


NP-Hard and NP-Complete  
X is NP-Hard, if ∀Y ∈ NP and Y ≤p X.  
X is NP-Complete, if X is NP-Hard and X  NP.

NPC problems are  
the most  
difficult NP  
problems.  
NPH problems  
do not have to be  
in NP.  
optimization

Not known if NPC problems can be solved by a deterministic TM in polynomial time

NPC = P
NPH = NPH
P = NP

NP-Completeness Proof Method  
To show that X is NP-Complete:  
1) Show that X is in NP  
2) Pick a problem Y, known to be an NP-Complete  
3) Prove Y ≤p X (reduce Y to X)  
Algorithm for Y  
Algorithm for X  
Y X  
Transf.  
yes  
no

Boolean Satisfiability Problem (SAT)  
A propositional logic formula is built from variables, operators AND  
(conjunction, ∧), OR (disjunction, ∨), NOT (negation, ¬), and parentheses:  
A formula is said to be satisfiable if it can be made TRUE by  
assigning appropriate logical values (TRUE, FALSE) to its variables.  
(X1 ∨ ¬X3) ∧ (X1 ∨ ¬X2 ∨ X4 ∨ X5) ∧ ...  
A formula is in conjunctive normal form (CNF) if it is a conjunction  
of clauses.  
A literal is a variable or its negation.  
A clause is a disjunction of literals.

CNF SAT is NP-complete.

Independent set
Given a graph, we say that a subset of vertices is  
“independent” if no two of them are joined by an  
edge.  
2  
4  
1  
53  
76  
The maximum independent set problem,  
MaxIndSet, asks for the size of the largest  
independent set in a given graph.

The maximum independent set problem
MaxIndSet is the size of the largest indedpendent set in a given graoh

oPTIMIZATION vERSON
mAXiIndeSEt is a optimization prloblem np-hard

Deicion version
Independentset of size k, is NPComplete?

Optimization vs. Decision Problems


f one can solve an optimization problem (in polynomial time), then  
one can answer the decision version (in polynomial time)  
Conversely, by doing binary search on the bound b, one can  
transform a polynomial time answer to a decision version into a  
polynomial time algorithm for the corresponding optimization  
problem  
In that sense, these are essentially equivalent.  
However, they belong to two different complexity classes.

Independent Set is NP Complete
Contain set of size k, at laeast k

Is it in NP?
Need to show we can verify sa solution in polynomial time
Given a set of vertices we can count them and verify that any two of them are not joind by an edge

Is it in NP hard
?

We need to pick Y such that y <p IOndSet for Y <= NP
Reduce from 3 SAT??
What is 3 sat

3sat is a sat where each claue has at most 3 literals

We construct a graph G that will have an independent set of size k  
iff the 3-SAT instance with k clauses is satisfiable.  
For each clause (X ⋁ Y ⋁ Z) we will be using a special gadget:  
Y  
Next, we need to connect gadgets.  
(X ⋁ Y ⋁ Z) ⋀ (X ⋁ ¬Y ⋁ Z) ⋀ (¬X ⋁ Y ⋁ ¬Z) ⋀ (¬X ⋁ ¬Y)  
As an example, consider the following instance: