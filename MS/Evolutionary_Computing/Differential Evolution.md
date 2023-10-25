# Differential Evolution

| Representation     | Real-valued vectors                                                                            |
| ------------------ | ---------------------------------------------------------------------------------------------- |
| Recombination      | Uniform crossover                                                                              |
| Mutation           | Differential mutation                                                                          |
| Parent Selection   | Given individual deterministically + Uniform random selection of the 3 necessary other vectors |
| Survivor Selection | Deterministic elitist replacement (parent vs child)                                            |
## Overview
- Developed: USA in 1995
- Early names: Storn, Price
- Typically applied to: Nonlinear and non differentiable real valued functions
- Attributed features:
	- populations are lists (sets where elements have a position)
	- four parents are needed to create a new individual
	- different variants exists due to changing the base vector 
- Special: differential mutation

## Differential Mutation
Given a population of candidate solution vectors in $\mathbb{R}^n$, for every candidate, create a new mutant vector. 
$$\bar{v}'=\bar{v}+\bar{p}$$
A new mutant is produced by adding a perturbation vector to the old one:
$$\bar{p}=F\cdot(\bar{y}-\bar{z})$$
where the perturbation vector p is the difference between vectors y and z, y and z are randomly chosen population members, and scaling factor F>0 (differential weight) is a real number.

## Uniform Crossover
DE uses uniform crossover with a crossover probability Cr that determines per position (gene) that the child inherits the value (allele) of the first parent. A restriction: at one randomly chosen position the child allele is taken from the first parent without making a random decision. This restriction implies that duplication of the second parent is not possible.

## Evolutionary Cycle
Population is a list $P=<\bar{u_1}, ..., \bar{u_{\mu}}>$ (ordering is not related to fitness value) 
1. Create a mutant vector population $M=<\bar{v_1}, ..., \bar{v_{\mu}}>$ where: 
	1. $v_i=a_i+ F(b_i-c_i)$
	2. and $a_i (≠ x_i)$ are randomly chosen base vectors from $P$. 
	3. $b_i$ and $c_i (≠ x_i)$ are chosen randomly from $P$ to define the difference vector. 
	4. $F$ is a scaling factor.
3. Create trial vector population $T=<\bar{u_1}, ..., \bar{u_{\mu}}>$ where $\bar{u_1}$ is made by uniform crossover between $\bar{x_1}$ and $\bar{v_1}$.
4. Deterministic selection applied to each pair $x_i$ and $u_i$ where the best of $x_i$ and $u_i$ is chosen to be the $i$-th individual in next generation controlling the rate at which the population evolves.

### Example (DE/rand/1/bin)
Minimize $f(x) = x_1 + x_2 + x_3$  
($x_i$ denotes an attribute of the fitness function)

- Step 0: initialize the population

|        | Individual 1 | Individual 2 | Individual 3 | Individual 4 | Individual 5 | Individual 6 |
| ------ | ------------ | ------------ | ------------ | ------------ | ------------ |:------------:|
| $x_1$  | 0.68         | 0.92         | 0.22         | 0.12         | 0.40         |     0.94     |
| $x_2$  | 0.89         | 0.92         | 0.14         | 0.09         | 0.81         |     0.63     |
| $x_3$  | 0.04         | 0.33         | 0.40         | 0.05         | 0.83         |     0.13     |
| $f(x)$ | 1.61         | 2.17         | 0.76         | 0.26         | 2.04         |     1.70     |

- Step 1: create a mutant vector population
	- For each $v_i$, choose $a_i$ (base), $b_i$ and $c_i$ randomly from the population $P$ 
	  different from $x_i$ ($x_i$ denotes a member of the population)
	- $v_i=a_i+ F(b_i-c_i)$, $F=0.8$

$i=1$, $b_1=$individual 2, $c_1=$ individual 4

| $x_i$ | $b_i$ | $-$ | $c_i$ | $=$ | $b_i - c_i$ | $F$  | $F(b_i-c_i)$ |
| ----- |:-----:| --- | ----- | --- | ----------- | ---- |:------------:|
| $x_1$ | 0.92  | -   | 0.12  | =   | 0.80        | 0.80 |     0.64     |
| $x_2$ | 0.92  | -   | 0.09  | =   | 0.83        | 0.80 |     0.66     |
| $x_3$ | 0.33  | -   | 0.05  | =   | 0.28        | 0.80 |     0.22     |

$i=1$, $a_1=$individual 6, $F(b_i-c_i)=$ from previous table

| $a_i$ | $+$ | $F(b_i-c_i)$ | $=$ | $v_i$ |
| ----- | --- | ------------ | --- |:-----:|
| 0.94  | +   | 0.64         | =   | 1.58  |
| 0.63  | +   | 0.66         | =   | 1.29  |
| 0.13  | +   | 0.22         | =   | 0.35  |

- Step 2: create trial vector population by crossover
	 - $u_i$ is made by uniform crossover between $x_i$ and $v_i$
	   (note: one allele is fixed from first parent)

 | $x_i$ |      | $v_i$ | $u_i$ |
 | ----- | ---- | ----- |:-----:|
 | $x_1$ | 0.68 | 1.58  | 1.58  |
 | $x_2$ | 0.89 | 1.29  | 0.89  |
 | $x_3$ | 0.04 | 0.35  | 0.04  |
 | f(x)  | 1.61 | 3.22  | 2.51  |

- Step 3: deterministically select best of $x_i$ and $u_i$
	- Thus keep $x_i$ (because we minimize)


## Different Variants
Different variants exists due to changing the base vector. The variant is described as DE/a/b/c where a, b, c are the placeholders for:
- **a** denotes the way to choose the base vector (rand or best)
- **b** is the number of difference vectors to define perturbation vector. E.g., with b = 2 we use two difference vectors and we’d get  $\bar{p}=F \cdot(\bar{y}- \bar{z} + \bar{y}'- \bar{z}')$
- **c** denotes the crossover scheme (“bin” is uniform crossover) 

DE/rand/1/bin is the notation for the version above.