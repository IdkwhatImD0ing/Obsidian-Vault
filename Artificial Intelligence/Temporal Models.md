Given expereince E from time 1 to T
We can infer
- Where am I now (estimation, filtering, localization)
- Where I will be at time t+k (prediction)
- where I was at time k < t (smooth)
- the probability of every state sequence that I went through (explanation)
- the most likely sequence of states I went through (Viterbi Algorithm)

## Where am I now?
### Forward Procedure
Main Idea: do not consider all possible state sequences, but every step in the experience and compute P(O|AMC) incrementally on time t:

### Backward Procedure
Similar to forward
But starting from the end and walking backwards

Finally, once you get alpha for all states at T, the state most likely is the state i that alpha(i) at t is highest

## Where I will be in the future?
Continue computing alpha values until you reach T+k

## Where I was at time k < t?
Given time 1 , ... ,k,k+1,...,t
best forward from 1 to k, best transition from k to k+1, best backward to k+1 from t

## The probability of every state sequence that I went through
They are the following states
t = 1; the state si such that a1(i) is the maximal
t = 2; the state si such that a2(i) is the maximal

t=T; the state si such that aT(i) is the maximal


