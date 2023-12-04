
# Evolutionary Programming

| Representation     | Real-valued vectors                          |
| ------------------ | ------------------------------------ |
| Recombination      | None                     |
| Mutation           | Gaussioan perturbation                             |
| Parent Selection   | Deterministic (each parent one offspring) |
| Survivor Selection | Probabilistic ($\mu+\mu$)                                     |

## Quick Overview
Developed in the USA in the 1960s by early names like L. Fogel. Typically applied to traditional EP for prediction by finite state machines and contemporary EP for (numerical) optimization. It's a very open framework where any representation and mutation operations are OK. It has been crossbred with ES (contemporary EP), making it hard to define what "standard" EP is. Special features include no recombination and standard self-adaptation of parameters (contemporary EP).

## Historical Perspective
EP aimed at achieving intelligence, where intelligence was viewed as adaptive behaviour. Prediction of the environment was considered a prerequisite to adaptive behaviour. Thus, the capability to predict is key to intelligence.

## Prediction by Finite State Machines
A finite state machine (FSM) consists of states S, inputs I, outputs O, and a transition function $\delta : S \times I \rightarrow S \times O$. It transforms an input stream into an output stream and can be used for predictions, e.g., to predict the next input symbol in a sequence.

Consider the FSM with: 
- S = {A, B, C}
- I = {0, 1}
- O = {a, b, c}
- $\delta$ given by a diagram 
![[EP_FSM1_img.png]]
### FSM as Predictor
Consider the following FSM with the task to predict the next input. The quality is measured as % of in(i+1) = outi. Given initial state C and input sequence 011101, it leads to output 110111 with a quality of 3 out of 5.
![[EP_FSM2_img.png]]
### Evolving FSMs to Predict Primes
P(n) = 1 if n is prime, 0 otherwise. I = N = {1,2,3,…, n, …}, O = {0,1}. Correct prediction: outi= P(in(i+1)). Fitness function: 1 point for correct prediction of next input, 0 point for incorrect prediction, penalty for "too many" states.

- **Parent selection:** each FSM is selected to be mutated once. 
- **Mutation operators** (one chosen randomly): change an output symbol, change a state transition (i.e., redirect edge), add a state, delete a state, change the initial state. 
- **Survivor selection:** ($\mu+\mu$). 
- **Results:** overfitting; after 202 inputs best FSM had one state and both outputs were 0, i.e., it always predicted "not prime". 
- **Main point:** not perfect accuracy but proof that simulated evolutionary process can create good solutions for intelligent tasks.

## Modern Evolutionary Programming
No predefined representation in general. Thus: no predefined mutation (must match representation). Often applies self-adaptation of mutation parameters.

### Representation
For continuous parameter optimization, chromosomes consist of two parts:
- Object variables: $x_1,…,x_n$
- Mutation step sizes: $\sigma_1,…,\sigma_n$
Full size: $\langle x_1,…,x_n, \sigma_1,…,\sigma_n \rangle$

### Mutation
Chromosomes: $\langle x_1,…,x_n, \sigma_1,…,\sigma_n \rangle$
- $\sigma_i' = \sigma_i \cdot (1 + \alpha \cdot N(0,1))$
- $x_i' = x_i + \sigma_i' \cdot N_i(0,1)$
- $\alpha \approx 0.2$
- Boundary rule: $\sigma' < \epsilon_0 \Rightarrow \sigma' = \epsilon_0$

Other variants proposed & tried:
- Using variance instead of standard deviation
- Mutate $\sigma$-last – BAD IDEA
- Other distributions, e.g., Cauchy instead of Gaussian

### Recombination 
None. Rationale: one point in the search space stands for a species, not for an individual and there can be no crossover between species. Much historical debate "mutation vs. crossover".

### Parent Selection
Each individual creates one child by mutation. Thus: deterministic and not biased by fitness.

## Evolving Checkers Players (Fogel'02)
Overall strategy: go to the position with the highest expected value. Neural nets for evaluating future values of moves are evolved. NNs have fixed structure with 5046 weights; these are evolved + one weight for "kings". Representation: vector of 5046 real numbers for object variables (weights), vector of 5046 real numbers for $\sigma$'s. Thus more than 10K variables to optimize. Mutation: Gaussian; lognormal scheme with $\sigma$-first plus special mechanism for the kings' weight; population size 15.

After tournament size q = 5 programs (with NN inside) play against other programs without human trainer or hard-wired intelligence – note the special character of the fitness function: no explicit formula. After 840 generations (6 months!) best strategy was tested against humans via Internet. Program earned "expert class" ranking outperforming 99.61% of all rated players.

## Summary
EP has less clear identity than GA and ES. Modern versions are hard to distinguish from ES. Branch is becoming less active/visible than other members of the EA family.
