# Evolution Strategies
## Quick Overview

Evolution Strategies were developed in Germany in the 1960s by early pioneers such as I. Rechenberg and H.-P. Schwefel. They are typically applied to numerical optimization.

### Key Features

- **Speed**: Evolution Strategies are known for their speed.
- **Optimization**: They are good optimizers for real-valued optimization.
- **Theory**: There is relatively much theory developed around Evolution Strategies.
- **Self-Adaptation**: Self-adaptation of (mutation) parameters is a standard feature in Evolution Strategies.
### ES technical summary tableau
| Representation     | Real-valued vectors                          |
| ------------------ | ------------------------------------ |
| Recombination      | Discrete or intermidieary                     |
| Mutation           | Gaussioan perturbation                             |
| Parent Selection   | Uniform random |
| Survivor Selection | ($\mu,\lambda$) or ($\mu+\lambda$)                                     |


# Evolution Strategies: (1+1) ES

The (1+1) Evolution Strategy (ES) is a simple yet effective method used in Evolution Strategies. It's often used for tasks that involve minimizing a function $f : R^n \rightarrow R$.

## Key Features

- **Algorithm**: This is a "two-membered ES" that uses vectors from $R^n$ directly as chromosomes.
- **Population Size**: The population size is 1.
- **Mutation**: Only mutation is used to create one child.
- **Selection**: Greedy selection is used.

## Mutation Mechanism in ES
This is an example with historical interest.
![[ES_norm_dist_img.png]]
In this example, $z$ values are drawn from a normal distribution $N(\xi,\sigma)$ where the mean $\xi$ is set to 0 and the variation $\sigma$ is called the mutation step size. 

The mutation step size $\sigma$ is varied on the fly by the "1/5 success rule". This rule resets $\sigma$ after every $k$ iterations as follows:

- $\sigma = \sigma / c$ if $p_s > 1/5$
- $\sigma = \sigma \cdot c$ if $p_s < 1/5$
- $\sigma = \sigma$ if $p_s = 1/5$

where $p_s$ is the percentage of successful mutations and $0.8 \leq c \leq 1$.

## Another historical example: the jet nozzle experiment
- Task: To optimize the shape of a jet nozzle
- Approach: random mutations to shape + selection
##### Initial shape
![[ES_jes_nozzle_init_img.png]]
##### Final Shape
![[ES_jes_nozzle_final_img.png]]

### Representation
Chromosomes consist of three parts:

1. **Object variables**: $x_1,…,x_n$
2. **Strategy parameters**:
    - Mutation step sizes: $\sigma_1,…,\sigma_n\sigma$
    - Rotation angles: $\alpha_1,…, \alpha_n\alpha$
3. Not every component is always present

Full size: $$\langle x_1,…,x_n, \sigma_1,…,\sigma_n ,\alpha_1,…, \alpha_k \rangle$$
where $k = \frac{n(n-1)}{2}$ (no. of i, j pairs)
### Recombination
Creates one child and acts per variable / position by either:
- Averaging parental values, or
- Selecting one of the parental values

From two or more parents by either:
- Using two selected parents to make a child
- Selecting two parents for each position independently 

The number of parents is random, but likely > 2.

#### Recombination operators

|                                         | Two fixed parents  | Two parents selected for each $i$ |
| --------------------------------------- | ------------------ | --------------------------------- |
| $z_i=(x_i+y_i)/2$                       | Local intermediary | Global intermediary               |
| $z_i$ is $x_i$ or $y_i$ chosen randomly | Local discrete     | Global discrete                                  |


# Parent Selection
Parents are selected by uniform random distribution whenever an operator needs one/some. Thus, ES parent selection is unbiased - every individual has the same probability to be selected.

# Self-adaptation
![[ES_self_adapt_img.png]]
Given a dynamically changing fitness landscape (location of the optimum is shifted every 200 generations), self-adaptive ES is able to:
- Follow the optimum and 
- Adjust the mutation step size after every shift!


## Prerequisites for Self-Adaptation
- $\mu > 1$ to carry different strategies
- $\lambda > \mu$ to generate offspring surplus 
- $(\mu,\lambda)$-selection to get rid of misadapted $\sigma$'s
- Mixing strategy parameters by (intermediary) recombination on them

## Example: The Cherry Brandy Experiment
Task: to create a color mix yielding a target color (that of a well-known cherry brandy). Ingredients: water + red, yellow, blue dye. Representation: $\langle w, r, y ,b \rangle$ no self-adaptation! Values scaled to give a predefined total volume (30 ml). Mutation: lo / med / hi $\sigma$ values used with equal chance. Selection: (1,8) strategy.

Fitness: students effectively making the mix and comparing it with target color – thus: so-called subjective selection. Termination criterion: student satisfied with mixed color. Solution is found mostly within 20 generations. Accuracy is very good. Note: this is an application without a quantifiable fitness value – also the case when breeding animals.

## Example: The Ackley Function, Bäck et al 93
The Ackley function (here used with n =30):
$$f(x)=-20 \cdot exp{(-0.2\sqrt{\frac{1}{n}\cdot\sum_{i=1}^{n}{x_i^2}} ) - exp{(\frac{1}{n}\sum_{i=1}^{n}{\cos{2\pi x_i}}) + 20 + e}}$$
Evolution strategy:
	Representation: 
	- $-30 < x_i < 30$ 
	- 30 step sizes
	- $(30,200)$ selection
	Termination : after 200000 fitness evaluations
	Results: average best solution is $7.48 \cdot 10^{-8}$ (very good)

# Summary
Evolution Strategies are very good for numerical optimization and can work with low computational budgets (low maximum of fitness evaluations) and high dimensional problems (large number of variables). Self-adaptation of (mutation) parameters is standard. Fewer parameters and design choices than in GAs. Many applications in business and industry. Hint: try the CMA-ES from Hansen (open source code), look out for recent variants.
