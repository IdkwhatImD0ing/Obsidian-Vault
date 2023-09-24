# Minimax Tree

Composed of Min and Max layers

### Max Layers

Simply maximizes the value of successors

### Min Layers

Same as min but just minimizes

## Problem:

Number of games states is exponential to the number of moves.

## Solution: Do not examine every node
• Alpha-beta pruning
• Remove branches that do not influence final decision

---
# Alpha Beta Tree and Pruning

Basic idea: “If you have an idea that is surely bad, don't take the time to see how truly awful it is.” -- Patrick Winston

## Alpha and Beta Values

Definition:
 - Alpha: The best (highest) value found so far for the maximizing player .
 - Beta: The best (lowest) value found so far for the minimizing player.

Max Layers set alpha value to max of beta value from children

Min Layers set beta value to min of alpha values from children

## How Values are Updated:

1. At the start, alpha is initialized to negative infinity (-∞) and beta to positive infinity (∞). This is because we haven't found any values for the maximizing or minimizing player yet.
2. When the search moves down the tree to a maximizing node, the algorithm keeps track of the best value found so far (highest). This value becomes the alpha value and is propagated to the node's children. If a child node has a higher alpha value, it will replace the current alpha value and be propagated further.
3. Similarly, when the search moves down the tree to a minimizing node , the algorithm keeps track of the best value found so far (lowest). This value becomes the beta value and is propagated to the node's children. If a child node has a lower beta value, it will replace the current beta value and be propagated further.
4. When the search moves back up the tree (backtracking), the algorithm updates the alpha or beta value based on the node's parent. If it's a maximizing node, the algorithm compares the current alpha value with the parent's beta value. If alpha is equal to or greater than beta, pruning occurs, and the search doesn't explore the remaining branches at that level.
5. If it's a minimizing node, the algorithm compares the current beta value with the parent's alpha value. If beta is equal to or less than alpha, pruning occurs, and the search doesn't explore the remaining branches at that level.



### Example:

![[Pasted image 20230222153759.png]]

WE DO NOT EXPAND PQR Because the First Max Node has a Value of -2, and we know that the second MAX NODE has to be above or equal to 1, since that is the min node of MNO branch. 