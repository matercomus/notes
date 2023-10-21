### Role
- Identifies individuals 
	- to become parents
	- to survive
- Pushes population towards higher fitness
- Usually probabilistic / stochastic
	- high quality solutions more likely to be selected than low quality
	- but not guaranteed
	- even worst in current population usually has non-zero probability of being selected
- This *stochastic* nature can help escape from local optima
# Selection can occur at two places:
- Individuals from current generation to take part in mating (parent selection)
- Individuals from parents + offspring to go into next generation (survivor selection)

Selection operators work on whole individuals, hence they are representation-independent.

There is a distinction between selection:
- Operators: Define selection probabilities
- Algorithms: Define how probabilities are implemented

This distinction is often forgotten or deemed irrelevant.

### Example: Roulette wheel selection
![[Roulette_wheel_selection_img.png]]
In principle, any selection mechanism can be used for parent selection as well as for survivor selection.



## Fitness-Proportionate Selection (FPS)
a.k.a Roulette Wheel (see above)

The probability for individual $i$ to be selected for mating in a population of size $\mu$ with FPS is 

$$P_{\text{fps}}(i) = \frac{f_i}{\sum_{j=1}^{\mu} f_j}$$
 
This method has problems including:
1. ==**Premature Convergence**:== One highly fit member can rapidly take over, if the rest of the population is much less fit and population members become (nearly) identical. When this happens too early, we can end up in a local optimum.
2. **Loss of selection pressure**: At the end of runs when fitness values are similar, EA can degrade to random search.
3. **Highly sensitive to function transposition**.

#### FPS and function transposition

| Individual | Fitness for f | Sel. Prob. for f | Fitness for f+10 | Sel. Prob. for f+10 | Fitness for f+100 | Sel. Prob. for f+100 |
| ---------- | ------------- | ---------------- | ---------------- | ------------------- | ----------------- | -------------------- |
| A          | 1             | 0.1              | 11               | 0.275               | 101               | 0.326                |
| B          | 4             | 0.4              | 14               | 0.35                | 104               | 0.335                |
| C          | 5             | 0.5              | 15               | 0.375               | 105               | 0.339                |
| SUM        | 10            | 1                | 40               | 1                   | 310               | 1                     |


## Parent Selection

#### Scaling
Scaling is a method used to adjust the fitness scores in genetic algorithms. There are two common types of scaling:

- **Windowing**: The new fitness $f'(i)$ is calculated as follows:
   $$f'(i) = f(i) - \beta$$
 where $\beta$ is the worst fitness in the last $n$ generations ($n=0$ refers to the current generation).

- **Sigma Scaling**: The new fitness $f'(i)$ is calculated as follows:
  $$f'(i) = \max\left(f(i) - \left(\bar{f} - c \cdot \sigma_f\right), 0\right)$$
$\bar{f}$ is the average fitness in the population,
$\sigma_f$ is the standard deviation of fitness,
$c$ is a constant.

This method tries to "flatten" selection pressure over the course of evolution.

#### Rank-based Selection
- Rank-based selection is an attempt to remove problems of FPS by basing selection probabilities on **relative** rather than absolute fitness. 
- The idea is to rank the population according to fitness and base selection probabilities on rank. 
- This imposes a sorting overhead on the algorithm, but this is usually negligible compared to the fitness evaluation time.

| Population size | $\mu$    |
| --------------- | -------- |
| Rank of best    | $\mu -1$ |
| ...             |          |
| Rank of worst   | 0        |

##### Linear Ranking
The probability of selection based on rank is given by:

$$P_{\text{lin-rank}}(i) = \frac{(2 - s)}{\mu} + \frac{(2i(s - 1))}{\mu(\mu - 1)}$$
This is parameterized by a factor $s$ where $1 < s \leq 2$. 
The parameter $s$ measures the advantage of the best individual.

For example, in a simple 3 member population:

| Individual | Fitness | Rank | $P_{selFP}$ | $P_{selLR}$ $(s=2)$ | $P_{selLR}$ $(s=1.5)$ |
| ---------- | ------- | ---- | ----------- | ------------------- | --------------------- |
| A          | 1       | 0    | 0.1         | 0                   | 0.167                 |
| B          | 4       | 1    | 0.4         | 0.33                | 0.33                  |
| C          | 5       | 2    | 0.5         | 0.67                | 0.5                   |
| SUM        | 10      | n/a  | 1.0         | 1.0                 | 1.0                      |
##### Explanation of calculation for individual B:
- **Fitness**: This is given in the problem. For individual B, the fitness is 4.
- **Rank**: This is based on the fitness of the individuals. The individual with the highest fitness gets the highest rank. In this case, individual B has the second highest fitness, so it gets a rank of 1.
- **$P_{selFP}$**: This is the selection probability for Fitness-Proportionate Selection (FPS). It's calculated as the fitness of the individual divided by the total fitness of all individuals. For individual B, it would be $4/10 = 0.4$.
- **$P_{selLR}$ $(s=2)$**: This is the selection probability for Linear Ranking when $s=2$. It's calculated using the formula: 
$$P_{\text{lin-rank}}(i) = \frac{(2 - s)}{\mu} + \frac{(2i(s - 1))}{\mu(\mu - 1)}$$
	Substituting $i=1$, $s=2$, and $\mu=3$ (the population size), we get:
$$P_{\text{lin-rank}}(1) = \frac{(2 - 2)}{3} + \frac{(2*1*(2 - 1))}{3*(3 - 1)} = 0.33$$
- **$P_{selLR}$ $(s=1.5)$**: This is similar to the previous calculation but with $s=1.5$. Substituting these values in, we get:
$$P_{\text{lin-rank}}(1) = \frac{(2 - 1.5)}{3} + \frac{(2*1*(1.5 - 1))}{3*(3 - 1)} = 0.333$$
	So, for individual B, the row would be:

| Individual | Fitness | Rank | $P_{selFP}$ | $P_{selLR}$ $(s=2)$ | $P_{selLR}$ $(s=1.5)$ |
| ---------- | ------- | ---- | ----------- | ------------------- | --------------------- |
| B          | 4       | 1    | 0.4         | 0.33                | 0.333                 |





##### Exponential Ranking
The formula for exponential ranking is given by:

$$P_{exp-rank}(i)=\frac{1-e^{-1}}{c}$$

```functionplot
---
title: Exponential Functions
xLabel: x
yLabel: y
bounds: [-10, 10, -1, 10]
disableZoom: 1
grid: true
---
g(x)=exp(-x)
f(x)=exp(x)
```

*Blue* $e^{-x}$
*Red* $e^{x}$

- **Linear Ranking**: It is limited in selection pressure.
- **Exponential Ranking**: This method can allocate more than 2 copies to the fittest individual.
- **Normalization**: The constant factor 'c' is normalized according to population size.

### Sampling algorithms

![[Sampling_alg_sel_img.png]]
Sampling mating pool from the selection probability distribution

### Tournament Selection
- All methods above rely on global population statistics
	- Could be a bottleneck especially on structured or very large populations
	- Relies on external fitness function which might not exist: e.g., evolving game playing strategies
 
- Idea for using only **local fitness information**:
	- Pick k members at random then select the best of these
	- Repeat to select more individuals
 
- Probability of selecting individual i  will depend on:
	- Rank of i
	- Size of sample k
		higher k increases selection pressure
	- Whether contestants are picked with replacement
		Picking without replacement increases selection pressure
- Whether fittest contestant always wins (deterministic) or this happens with probability p

#### Uniform Parent Selection
$$P_{uniform}(i)=\frac{1}{\mu}$$
Uniform parent selection is a method used in genetic algorithms where parents are selected by a uniform random distribution whenever an operator needs one or more individuals. This method is unbiased, meaning every individual has the same probability to be selected, regardless of their fitness score.
##### Key Characteristics
- **Unbiased Selection**: In uniform parent selection, every individual in the population has an equal chance of being selected. This is different from methods like roulette wheel or tournament selection, where individuals with higher fitness scores have a higher chance of being selected.

- **Large Populations**: When working with extremely large populations, a phenomenon known as over-selection can occur. Over-selection happens when a small subset of the population with the highest fitness scores is selected too often, leading to a loss of diversity in the population. Uniform parent selection can help mitigate this issue by ensuring all individuals have an equal chance of being selected.

- **Usage**: Uniform parent selection is particularly useful when you want to maintain diversity in your population or when the fitness landscape is deceptive (i.e., the global optimum is surrounded by low fitness regions).

## Survivor Selection
Survivor selection is a crucial step in genetic algorithms where we select **$μ$ individuals** to form the next generation from **$μ$ parents** and **$λ$ offspring**.
#### Key Concepts
- **Parent Selection Mechanisms**: The mechanisms used for parent selection can also be utilized for selecting survivors.
- **Survivor Selection Approaches**: Survivor selection can be divided into two main approaches:
	- **Fitness-based Selection**: In this approach, the fitness of an individual plays a crucial role in its selection. The individuals with higher fitness have a higher chance of being selected.

	- **Age-based Selection**: In this approach, the age of an individual is the primary factor for its selection. Fitness is not taken into account. In Steady State Evolutionary Algorithms (SSEA), this can be implemented as "delete-random" (not recommended) or as first-in-first-out (a.k.a. delete-oldest).

### Fitness-based Survivor Selection
Fitness-based survivor selection is a method used in genetic algorithms where the fitness of an individual plays a crucial role in its selection. The individuals with higher fitness have a higher chance of being selected.
#### Key Concepts
- **Elitism**: This approach always keeps at least one copy of the fittest solution so far. It is widely used in both population models (generational, steady-state). Elitism can keep more than one "champion", e.g., the best $N$ individuals or the best $x$ %.

- **Delete Worst (a.k.a. GANITOR)**: This approach is from Whitley's original Steady-State algorithm (he also used linear ranking for parent selection). It can lead to rapid takeover, so it's recommended to use with large populations or "no duplicates" policy.

- **Round-robin Tournament**: In this approach, $P$ is the set of $μ$ parents, $O$ is the set of $λ$ offspring. Pairwise competitions in round-robin format are conducted where each solution $x$ from $P \cup O$ is compared with $q$ other randomly chosen solutions. For each comparison, a "win" is assigned to $x$ if it is better than its opponent. The $μ$ solutions with the greatest number of wins are selected to be parents of the next generation. The parameter $q$ allows tuning selection pressure. Typically, $q = 10$.


- **$(\mu,\lambda)$-selection a.k.a. "Comma Strategy"**: This approach is based on the set of children only ($\lambda > \mu$). The best $\mu$ out of $\lambda$ are chosen.

- **$(\mu+\lambda)$-selection a.k.a. "Plus Strategy"**: This approach is based on the set of parents and children. The best $\mu$ out of $\mu+\lambda$ are chosen.

	Often, $(\mu,\lambda)$-selection is preferred because it can forget and hence it is better in leaving local optima and it is better in following moving optima. Using the + strategy, bad $\sigma$ values can survive in ⟨x,$\sigma$⟩ too long if their host x is very fit. $\lambda \approx 7 \cdot \mu$ is a traditionally good setting (but $\lambda \approx 3 \cdot \mu$ seems more popular lately).

## Selection Pressure
Selection pressure is a crucial concept in genetic algorithms. It can be quantified using the takeover time $\tau^{*}$, which is the number of generations it takes until the application of selection completely fills the population with copies of the best individual.
#### Key Concepts
- **Takeover Time**: Goldberg and Deb showed (for evolution strategies) that the takeover time can be calculated using the following formula:
$$\tau^{*}=\frac{\ln \lambda}{\ln(\lambda/\mu)}$$
- **Specific Values**: Here are some specific values for different strategies:
	- An evolution strategy with $\mu = 15$ and $\lambda = 100$: $\tau^{*} \approx 2$
	- A GA with proportional selection: $\tau^{*} = 460$