## Models with Actions and Sensors (POMDP)

Partial Observable Markov Decision Processes (POMDPs) are used to model decision-making problems where the state of the system is not fully observable. Given experience \( E \) from time 1 to \( T \), we can infer several things:

1. **Where am I now? (Estimation, Filtering, Localization)**
   - This involves determining the current state of the system based on the observations and actions up to the current time.

2. **Where will I be at time \( t+k \)? (Prediction)**
   - This refers to forecasting future states of the system based on current and past observations.

3. **Where was I at time \( k < t \)? (Smoothing)**
   - Smoothing refers to inferring past states of the system given observations up to the current time.

4. **The probability of every state sequence that I went through (Explanation)**
   - This involves computing the probabilities of all possible state sequences that could have led to the current observation.

5. **The most likely sequence of states I went through (Viterbi Algorithm)**
   - The Viterbi Algorithm is used to find the most probable sequence of hidden states.

## Detailed Analysis:

### Where Am I Now?
- **Forward Procedure**
  - The main idea here is to compute the probability of the observation sequence given the model, denoted as \( P(O|\lambda) \), incrementally over time \( t \). This is achieved by considering only the current state and the previous state, rather than all possible state sequences.

### Backward Procedure
- Similar to the forward procedure, but it starts from the end of the observation sequence and works backwards.
- The final state likelihood is determined by identifying the state \( i \) for which the backward probability \( \beta(i) \) at time \( t \) is highest.

### Where Will I Be in the Future?
- Continue computing forward probabilities (alpha values) until reaching time \( T+k \).

### Where Was I at Time \( k < t \)?
- This involves combining the forward probabilities up to time \( k \), the transition probabilities from time \( k \) to \( k+1 \), and the backward probabilities from time \( t \) to \( k+1 \).

### The Probability of Every State Sequence
- This is typically done by iterating over time steps and selecting the state \( s_i \) for each time \( t \) that maximizes the forward probability \( \alpha_t(i) \).

### Additional Considerations:
- **Model Parameters**: POMDPs are defined by their state space, action space, observation space, transition model, observation model, and reward function.
- **Belief State**: In POMDPs, the exact state is not known, so a belief state (probability distribution over possible states) is maintained.
- **Value Iteration**: An important method in POMDPs for computing the optimal policy.

