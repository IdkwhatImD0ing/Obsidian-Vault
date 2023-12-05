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

Your additional notes on temporal models are a good start. I'll expand on each model to provide a more comprehensive understanding.

# Other Temporal Models
### Markov Chains
- **Definition**: A Markov Chain is a stochastic model describing a sequence of possible events in which the probability of each event depends only on the state attained in the previous event.
- **Characteristics**: 
  - Discrete state space.
  - Time-homogeneous transitions, meaning the transition probabilities are independent of time.
- **Application**: Used in various fields like finance, economics, and natural language processing for modeling random systems that change states over time.

### Hidden Markov Model (HMM)
- **Definition**: An HMM is a statistical model where the system being modeled is assumed to follow a Markov process with hidden states.
- **Characteristics**: 
  - Set of hidden states, observed data, and a model of the state transitions, observation likelihood, and initial state distribution.
  - Useful in temporal pattern recognition such as speech, handwriting, gesture recognition, part-of-speech tagging, and bioinformatics.
- **Differences from Markov Chains**: In HMMs, the state is not directly visible, but the output, dependent on the state, is visible.

### Dynamic Bayesian Networks (DBNs)
- **Definition**: DBNs are a general model for stochastic processes. They extend Bayesian networks by modeling temporal sequences.
- **Characteristics**: 
  - Composed of a sequence of Bayesian networks, one for each time slice.
  - Can represent both discrete and continuous variables.
- **Application**: Used in robotics, speech recognition, biology, and others for modeling time-varying phenomena.

### Continuous State Models
- **Definition**: These models deal with systems where the state space is continuous.
- **Characteristics**: 
  - State transitions may involve probabilistic functions or differential equations.
  - Often used in conjunction with techniques like Kalman filters.
- **Application**: Relevant in fields like robotics, physics, and economics where the systems have continuous dynamics.

### Partially Observable Markov Decision Processes (POMDPs)
- **Definition**: POMDPs are an extension of Markov decision processes (MDPs) to include observation and information gathering.
- **Characteristics**: 
  - Includes a set of states, a set of actions, a set of observations, transition probabilities, observation probabilities, and reward functions.
  - Models decision-making in uncertain, dynamic environments.
- **Applications**: Useful in areas like robotics, automated control, and economics.