Review:
n 1936 Alan Turing described:  
• A simple formal model of computation now known as Turing machines.  
• A proof that TM can NOT solve the halting problem.  
• A proof that NO Turing machine can determine whether a given  
proposition is provable from the axioms of first-order logic.  
• Compelling arguments that a problem not computable by a Turing  
machine is not “computable” in the absolute (human) sense.  
• A non-deterministic Turing machine: for each state it makes an  
arbitrary choice between a finite of possible transitions.
Non-Deterministic Turing Machine  
• NDTM is a choice machine: for each state it makes an arbitrary  
choice between a finite (possibly zero) number of states.  
• The computation of a NDTM is a tree of possible configuration paths.  
• One way to visualize NDTM is that it makes an exact copy of itself  
for each available transition, and each machine continues the  
computation.  
• Rabin & Scott in 1959 shown that adding non-determinism does not  
result in more powerful machine.  
• For any NDTM, there is a DTM that accepts and rejects exactly the  
same strings as NDTM.  
• P vs. NP is about whether we can simulate NDTM in polynomial time.
Complexity Classes  
P = set of problems that can be solved in polynomial time by a DTM.  
NP = set of problems for which solution can be verified in  
polynomial time by a deterministic TM.  
X is NP-Hard, if ∀Y ∈ NP and Y ≤p X.  
X is NP-Complete,  
if X is NP-Hard and X  NP.  
NP = set of problems that can be solved in polynomial time by a NDTM.

It’s not known if NPC problems can be solved by a deterministic TM in  
polynomial time.  
NPC problems are  
the most  
difficult NP  
problems.  
optimization &  
decision  
problems  
NPC problems can be solved by a non-deterministic TM in polynomial  
time.


NP-Completeness Proof Method  
To show that X is NP-Complete:  
1) Show that X is in NP  
2) Pick a problem Y, known to be an NP-Complete  
3) Prove Y ≤p X (reduce Y to X)  
In lecture 11 we have proved that Independent Set  
is NP-Complete by reduction from 3-SAT (3SAT ≤p IndSet)  
Reduction from 3SAT to IndSet consists of three parts:  
• we transform an arbitrary CNF formula into a special graph G and a  
specific integer k, in polynomial time.  
• we transform an arbitrary satisfying assignment for 3SAT into an  
independent set in G of size k.  
• we transform an arbitrary independent set (in G) of size k into a  
satisfying assignment for 3SAT.

Vertex Cover  
Given G=(V,E), find the smallest S⊂V s.t. every  
edge is incident to vertices in S.  
The minimum vertex cover problem, MinVC, asks  
for the size of the smallest vertex cover in a  
given graph.

Decision version
Given f and k, does G contain a vc of size vc <= k

Theorem for a graph G Ve S is an independent set if and only if vs is a vertex cover

Forward Proof
Given S is an IS


x in IS then y not in Is if follows and y is in VC
if y in Is then x not in Is if follows and x in vc
x y both not in IS then x y in VC

Backwards proof
Given a vc
Pick for all x y s.t x not in VC y in VC
There exists edge x, y, does not proof by contradiction

it follows x, y in IS


Min Vertex Cover in NP-Hard  
Claim: a graph G=(V,E) has an independent set of size at least k if and  
only if G has a vertex cover of size at most V-k.  
MaxIndSet ≤p MinVC  
Ind. Set ≤p Vertex Cover  
Vertex Cover in NP-Complete  
By the previous theorem.  
By the previous theorem.

Hamiltonian Cycle Problem  
A Hamiltonian cycle (HC) in a graph is a cycle that  
visits each vertex exactly once.  
Problem Statement:  
Given a directed or undirected graph G = (V,E). Find if  
the graph contains a Hamiltonian cycle.  
We can prove it that HC problem is NP-complete by reduction from  
SAT, but we won’t.

ssuming that finding a Hamiltonian Cycle (HC) in a graph is NP-  
complete, prove that finding a Hamiltonian Path is also NP-  
complete. HP is a path that visits each vertex exactly once and  
isn’t required to return to its starting point.


HP in NP verify in polynomial time

NP in NPH
construct a polynomial maping
make a claim
prove the claim in both directions

