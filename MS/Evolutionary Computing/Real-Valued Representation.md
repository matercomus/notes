## General Scheme of Floating Point Mutations

In the context of genetic algorithms, a mutation is a small, random tweak in the chromosome, meant to add diversity to the population. For floating-point representations, this could mean adding a small random value to the current value of the gene.

Let's denote the original gene value as $x$ and the mutated gene value as $x'$.

If $x$ is a vector of length $l$, then we can represent it as follows:

$$\bar{x}=<x_1,...,x_l> \implies \bar{x}'=<x_1',...,x_l'>$$

Each $x_i$ and $x_i'$ belongs to an interval $[LB_i,UB_i]$:

$$x_i,x_i'\in [LB_i,UB_i]$$
## Uniform Mutation

In uniform mutation, the new gene value $x'$ is drawn randomly from a uniform distribution within a specified lower bound (LB) and upper bound (UB).

Mathematically, this can be represented as:

$$x_i' \sim U[LB_i, UB_i]$$

where $U[LB_i, UB_i]$ denotes a uniform distribution between LB and UB.

This method is analogous to bit-flipping in binary representations or random resetting in integer representations.

### Example

Let's say we have a gene that represents the size of a bird's beak and it's currently set to 5.0 cm. If we apply uniform mutation with LB = 1 cm and UB = 10 cm, the new gene value could be any number between 1 and 10. For instance, it might become 7.3 cm or 2.6 cm - it's completely random!


## Non-uniform Mutation
- Many methods proposed, such as time-varying range of change etc.
- Most schemes are probabilistic but usually only make a small change to value
- Most common method is to add random noise to each variable separately, taken from $N(0,\sigma)$ Gaussian distribution and then curtail to range
$$x_i' = x_i + N(0,\sigma)$$
- Standard deviation $\sigma$ is the mutation step size, controls amount of change (2/3 of random drawings will lie in range (- $\sigma$ to + $\sigma$))

## Self-Adaptive Mutation
Self-adaptive mutation is a technique used in genetic algorithms to adjust the mutation step size, $\sigma$, dynamically based on the fitness of the solutions. Here are some key points:

- In self-adaptive mutation, $\sigma$ is mutated first.
- The net mutation effect transforms the pair $\langle x, \sigma \rangle$ into $\langle x', \sigma' \rangle$.
- The order of mutation is important:
	- First, $\sigma$ is mutated to $\sigma'$.
	- Then, $x$ is mutated to $x'$ using the equation $x' = x + N(0,\sigma')$.

The rationale behind this order is that the new pair $\langle x', \sigma' \rangle$ is evaluated twice:
- Primary evaluation: $x'$ is considered good if $f(x')$ (the fitness of $x'$) is good.
- Secondary evaluation: $\sigma'$ is considered good if the $x'$ it created has a good fitness.

Reversing the mutation order would not yield the same results.

## Uncorrelated Mutation with One σ
In uncorrelated mutation with one σ, each chromosome is represented as $\langle x_1,...,x_n, \sigma \rangle$. The mutation process is as follows:

- First, $\sigma$ is mutated to $\sigma'$ using the equation $\sigma' = \sigma \cdot \exp(\tau \cdot N(0,1))$.
- Then, each $x_i$ is mutated to $x'_i$ using the equation $x'_i = x_i + \sigma' \cdot N_i(0,1)$.

Here, $\tau$ is the learning rate and is typically close to $1/\sqrt{n}$ (symbolized as $\tau \approx 1/\sqrt{n}$).

Additionally, there is a boundary rule: if $\sigma' < \epsilon_0$, then $\sigma' = \epsilon_0$. This ensures that the mutation step size does not become too small.

#### Mutants with equal likelihood
![[Uncorr_mut_one_sigma_img.png]]
Circle: mutants having the same chance to be created

## Uncorrelated Mutation with n σ's in Genetic Algorithms
In uncorrelated mutation with n σ's, each chromosome is represented as $\langle x_1,...,x_n, \sigma_1,..., \sigma_n \rangle$. The mutation process is as follows:

- First, each $\sigma_i$ is mutated to $\sigma'_i$ using the equation $\sigma'_i = \sigma_i \cdot \exp(\tau' \cdot N(0,1) + \tau \cdot N_i (0,1))$.
- Then, each $x_i$ is mutated to $x'_i$ using the equation $x'_i = x_i + \sigma'_i \cdot N_i (0,1)$.

Here, $\tau'$ and $\tau$ are the learning rates. Specifically:
- $\tau'$ is the overall learning rate and is typically close to $1/(2\sqrt{n})$ (symbolized as $\tau' \approx 1/(2\sqrt{n})$).
- $\tau$ is the coordinate-wise learning rate and is typically close to $1/\sqrt{2\sqrt{n}}$ (symbolized as $\tau \approx 1/\sqrt{2\sqrt{n}}$).

Additionally, there is a boundary rule: if $\sigma'_i < \epsilon_0$, then $\sigma'_i = \epsilon_0$. This ensures that the mutation step size does not become too small.

#### Mutants with equal likelihood
![[Uncorr_mut_n_sigma_img.png]]
Ellipse: mutants having the same chance to be created


# Correlated Mutations

In correlated mutations, each chromosome is represented as $\langle x_1,...,x_n, \sigma_1,..., \sigma_n ,\alpha_1,..., \alpha_k \rangle$, where $k = n \cdot (n-1)/2$.

The covariance matrix $C$ is defined as follows:
- $c_{ii} = \sigma_i^2$
- $c_{ij} = 0$ if $i$ and $j$ are not correlated
- $c_{ij} = 0.5 \cdot (\sigma_i^2 - \sigma_j^2) \cdot \tan(2\alpha_{ij})$ if $i$ and $j$ are correlated

Please note the numbering/indices of the $\alpha$'s.

The mutation mechanism in genetic algorithms can be described as follows:

- Each $\sigma_i$ is mutated to $\sigma'_i$ using the equation $\sigma'_i = \sigma_i \cdot \exp(\tau' \cdot N(0,1) + \tau \cdot N_i (0,1))$.
- Each $\alpha_j$ is mutated to $\alpha'_j$ using the equation $\alpha'_j = \alpha_j + \beta \cdot N (0,1)$.
- The vector $x$ is mutated to $x'$ using the equation $x' = x  + N(0,C')$, where $x$ stands for the vector $\langle x_1,...,x_n \rangle$ and $C'$ is the covariance matrix $C$ after mutation of the $\alpha$ values.

The learning rates are typically close to the following values:
- $\tau' \approx 1/(2\sqrt{n})$
- $\tau \approx 1/\sqrt{2\sqrt{n}}$
- $\beta \approx 5°$

Additionally, there are boundary rules:
- If $\sigma'_i < \epsilon_0$, then $\sigma'_i = \epsilon_0$.
- If $|\alpha'_j| > \pi$, then $\alpha'_j = \alpha'_j - 2\pi\cdot\text{sign}(\alpha'_j)$.

Note: This mechanism is used in the Covariance Matrix Adaptation Evolution Strategy (CMA-ES), one of the best EAs for numerical optimization (open source!).

#### Mutants with equal likelihood
![[Corr_mut_img.png]]
Ellipse: mutants having the same chance to be created


# Recombination

Recombination is a key process in genetic algorithms that combines the genetic information of two parents to generate new offspring. There are several types of recombination:

## Discrete Recombination

In discrete recombination, each allele value in the offspring $z$ comes from one of its parents $(x,y)$ with equal probability. This can be represented as $z_i = x_i$ or $y_i$. This method could use n-point or uniform crossover.

## Intermediate Recombination

**Intermediate recombination** exploits the idea of creating children "between" parents, hence it's also known as **arithmetic recombination**. It can be represented as $z_i = \alpha x_i + (1 - \alpha) y_i$, where $0 \leq \alpha \leq 1$.

The parameter $\alpha$ can be:
- Constant: This is known as uniform arithmetical crossover.
- Variable: For example, it could depend on the age of the population.
- Random: It could be picked at random every time.

## Single Arithmetic Crossover
![[Single_arithmetic_xover_img.png]]
In single arithmetic crossover, given two parents $\langle x_1,...,x_n \rangle$ and $\langle y_1,...,y_n \rangle$, a single gene $k$ is chosen at random. The offspring (child1 and child2) are then created as follows:

Child 1:
$$\langle x_1,...,x_{k-1}, \alpha y_k + (1- \alpha)x_k, x_{k+1}, ..., x_n \rangle$$

Child 2:
$$\langle y_1,...,y_{k-1}, \alpha x_k + (1- \alpha)y_k, y_{k+1}, ..., y_n \rangle$$

Here, $\alpha$ can be a constant or chosen at random for each crossover. This means that the $k$-th gene of the offspring is a weighted average of the $k$-th genes of its parents, while all other genes are inherited from the respective parent.

For example, let's say we have two parents $x = \langle 1, 2, 3 \rangle$ and $y = \langle 4, 5, 6 \rangle$, and we choose $k=2$ and $\alpha=0.5$. The offspring would be:

Child 1: $$\langle 1, 0.5*5 + 0.5*2, 3 \rangle = \langle 1, 3.5, 3 \rangle$$
Child 2: $$\langle 4, 0.5*2 + 0.5*5, 6 \rangle = \langle 4, 3.5, 6 \rangle$$

## Simple Arithmetic Crossover
![[Simple_arithmetic_xover_img.png]]
In simple arithmetic crossover, given two parents $\langle x_1,...,x_n \rangle$ and $\langle y_1,...,y_n \rangle$, a single gene $k$ is chosen at random. After this point, the genes are mixed to create the offspring (child 1 and child 2) as follows:

Child 1:
$$\langle x_1, ..., x_k, \alpha y_{k+1}+(1- \alpha) x_{k+1}, ..., \alpha y_n +  (1- \alpha) x_n \rangle$$

Child 2:
$$\langle y_1, ..., y_k, \alpha x_{k+1}+(1- \alpha) y_{k+1}, ..., \alpha x_n +  (1- \alpha) y_n \rangle$$

Here, $\alpha$ can be a constant or chosen at random for each crossover. This means that the genes after the $k$-th gene of the offspring are a weighted average of the corresponding genes of its parents.

For example, let's say we have two parents $x = \langle 1, 2, 3 \rangle$ and $y = \langle 4, 5, 6 \rangle$, and we choose $k=2$ and $\alpha=0.5$. The offspring would be:

Child 1: $$\langle 1, 2, 0.5*6 + 0.5*3 \rangle = \langle 1, 2, 4.5 \rangle$$
Child 2: $$\langle 4, 5, 0.5*3 + 0.5*6 \rangle = \langle 4, 5, 4.5 \rangle$$
$$\alpha \bar{x} + (1- \alpha ) \bar{y}$$

## Whole Arithmetic Crossover
![[whole_arithmetic_xover_img.png]]
Whole arithmetic crossover is a commonly used recombination method in evolutionary computation algorithms. Given two parents $\bar{x} = \langle x_1,...,x_n \rangle$ and $\bar{y} = \langle y_1,...,y_n \rangle$, the offspring (child1 and child2) are created as follows:

Child 1:
$$\alpha \bar{x} + (1- \alpha ) \bar{y}$$

Child 2:
$$\alpha \bar{y} + (1- \alpha ) \bar{x}$$

Here, $\alpha$ can be a constant or chosen at random for each crossover. This means that each offspring is a weighted average of its parents.

For example, let's say we have two parents $\bar{x} = \langle 1, 2, 3 \rangle$ and $\bar{y} = \langle 4, 5, 6 \rangle$, and we choose $\alpha=0.5$. The offspring would be:

Child 1: $$0.5*\langle 1, 2, 3 \rangle + 0.5*\langle 4, 5, 6 \rangle = \langle 2.5, 3.5, 4.5 \rangle$$
Child 2: $$0.5*\langle 4, 5, 6 \rangle + 0.5*\langle 1, 2, 3 \rangle = \langle 2.5, 3.5, 4.5 \rangle$$
## Blend Crossover
Blend crossover is a recombination method used in evolutionary computation algorithms. Given two parents $\langle x_1,...,x_n \rangle$ and $\langle y_1,...,y_n \rangle$, where $x_i < y_i$, the offspring is created as follows:

- Calculate $d_i = y_i - x_i$.
- Randomly sample $z_i$ from the interval $[x_i, y_i]$.
- Randomly sample $z_i$ from the interval $[x_i - \alpha d_i, y_i + \alpha d_i]$.

Here, $\alpha$ is a parameter that controls the extent of the blending. The original authors found that $\alpha = 0.5$ yielded the best results.



## Overview different possible offspring
![[Overview_possible_offspring_img.png]]
- Single arithmetic:  $\set{s_1, s_2, s_3, s_4}$
- Whole arithmetic: inner box (w if alpha = 0.5)
- Blend crossover: outer box 

## Multi-Parent Recombination
In the context of evolutionary computation algorithms, we are not restricted by the "practicalities" of nature. While mutation uses $n = 1$ parent and traditional crossover uses $n = 2$ parents, the extension to $n > 2$ is a natural progression to examine.

Multi-parent recombination has been around since the 1960s. Although it's still rare, studies indicate that it can be useful in certain contexts. This method involves combining the genetic information of more than two parents to generate new offspring.


### Type 1
![[Multi_parent_recombination_img.png]]
The idea behind this type of multi-parent recombination is to segment and recombine the parents. Here's an example of how it works, using a method called diagonal crossover for $n$ parents:

- Choose $n-1$ crossover points, which are the same in each parent.
- Compose $n$ children from the segments of the parents along a "diagonal", wrapping around as necessary.

This operator generalizes 1-point crossover, extending it to more than two parents.

### Type 2

The idea behind this type of multi-parent recombination is to perform an arithmetical combination of the alleles, which are assumed to be real-valued. Here's an example of how it works, using a method called arithmetic crossover for $n$ parents:

- The $i$-th allele in the child is the average of the parents' $i$-th alleles.

This method creates a child that is at the "center of mass" of its parents. While this might seem odd in the context of genetic algorithms, it has been known and used for a long time in evolution strategies, where it's called intermediary recombination.

## QUESTION
What would be the multi-parent equivalent of uniform crossover?
Would that belong to Type 1, Type 2, or a new type?

Possible answer:
### Type 3 Multi-Parent Recombination: Uniform Crossover

Given $n$ parents $\langle x_{1,1},...,x_{1,n} \rangle$, ..., $\langle x_{n,1},...,x_{n,n} \rangle$, the offspring is created as follows:

- For each allele $i$, randomly select one parent $j$ and set $z_i = x_{j,i}$.

This method generalizes uniform crossover to more than two parents. It maintains the diversity-promoting property of uniform crossover while potentially exploring a larger portion of the search space.
