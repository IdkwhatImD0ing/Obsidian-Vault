# Minimax Tree

## Layers
- **Max Layers**: Maximize the value among child nodes.
- **Min Layers**: Minimize the value among child nodes.

## Issue
- Exponential growth in game states with respect to moves.

## Solution
- Use Alpha-Beta Pruning to ignore irrelevant branches.

---

# Alpha-Beta Pruning

Basic idea: “If you have an idea that is surely bad, don't take the time to see how truly awful it is.” -- Patrick Winston

## Concept
- Ignore branches that won't affect the final decision.

## Alpha and Beta
- **Alpha**: Best value (highest) for maximizing player.
- **Beta**: Best value (lowest) for minimizing player.
- Max Layers set alpha value to max of beta value from children
- Min Layers set beta value to min of alpha values from children

## Value Update Rules
1. Initialize alpha to -∞, beta to ∞.
2. At a Max node, update alpha if a child has a higher value.
3. At a Min node, update beta if a child has a lower value.
4. Prune branches where alpha >= beta during backtracking.
### Example:

![[Pasted image 20230222153759.png]]

WE DO NOT EXPAND PQR Because the First Max Node has a Value of -2, and we know that the second MAX NODE has to be above or equal to 1, since that is the min node of MNO branch. 