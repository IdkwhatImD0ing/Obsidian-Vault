
Sometimes, classification is not.

Problem: Decide whether to wait for a table at a restraunt, based on the following attributes/features

Leaves of the tree of decisions
Nodes are questions. 
- Are there alternative restraunts
- Is the a comfortable bar area to wait in
- Is today Friday or Saturday
- Are we hungry?
- HOw mayn epeople are in the restraunt
- Whats the price
- etc
- 

### Inductive Learning of Decision Tree

Simplest: Construct a decision tree with one leaf for every example
Memory based learning, not good generalizaton

Advanced. split on each variable so that the purity of each split increases, eithe ronly yes or only no

Puyrety measure with entropy
Entropy = iP(Yes)ln[P(yes)]-P(no)ln[P(no)]

### How many distinct decision trees with n boolean attributes?
Number of boolean funciton
NUmber of distinct truth tables with 2^n rules = 2^2^n

# ID3
