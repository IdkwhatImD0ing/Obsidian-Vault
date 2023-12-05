Given expereince E from time 1 to T
We can infer
- Where am I now (estimation, filtering, localizaiton)
- Where I will be at time t+k (prediction)
- where I was at time k < t (smooth)
- the probability of every state sequence that I went through (explanation)
- the most likely sequence of states I went through (Viterbi Algorithm)

## Forward Procedure
Main Idea: do not consider all possible state sequences, but every step in the experience and compute P(O|AMC) incrementally on time t:
