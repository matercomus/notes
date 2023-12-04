# Particle Swarm Optimization (PSO)

| Representation     | Real-valued vectors                                            |
| ------------------ | -------------------------------------------------------------- |
| Recombination      | None                                                           |
| Mutation           | Adding velocity vector                                         |
| Parent Selection   | Deterministic (each parent creates one offspring via mutation) |
| Survivor Selection | Generational (offspring replaces parents)            |

## Overview
- Developed: in 1995
- Early names: Kennedy, Eberhart
- Typically applied to: Optimising nonlinear functions
- Attributed features:
	- No crossover
	- Every candidate solution carries its own perturbation vector
- Special:
	- Inspired by social behavior of bird flocking/fish schooling
	- Particles with location and velocity instead of individuals with genotype and mutation 

## Main Idea
Every population member / individual is a pair $<\bar{x}, \bar{p}>$ where: 
- $\bar{x}$ is a solution vector in $\mathbb{R}^n$
- $\bar{p}$ is a perturbation vector in $\mathbb{R}^n$ of this
The perturbation vector determines how the solution vector is changed to produce a new one: $\bar{x}'=\bar{x}+\bar{p}'$

## Representation + Variation Sketch
Every particle (= population member = individual) is a pair of 
- $\bar{x}$ is a position vector (location) in $\mathbb{R}^n$
- $\bar{v}$ is a velocity vector in $\mathbb{R}^n$
New velocity vector is the weighted sum of 3 components:
- Current velocity vector $\bar{v}$  
- Vector from current position to best past position of this particle
- Vector from current position to best past position of the population 

The formula for the new velocity vector is:
$$\bar{v}'=weight1 \cdot \bar{v}+weight2 \cdot (\bar{y}-\bar{x}) + weight3 \cdot (\bar{z}-\bar{x})$$
![[PSO_vis_img.png]]
## Detailed Representation + Variation
A particle = individual = population member i is a 3-tuple $<\bar{x}_i, \bar{v}_i, \bar{b}_i>$ of:
- position vector (location) $\bar{x}_i$
- velocity vector $\bar{v}_i$
- best position vector of this particle in the past $\bar{b}_i$

Each triple is replaced by the mutant triple $<\bar{x}_i, \bar{v}_i, \bar{b}_i> \implies <\bar{x}_i', \bar{v}_i', \bar{b}_i'>$ where:
$$\bar{x}'_i=\bar{x}+\bar{v}_i'$$
$$\bar{v}_i'= w \cdot \bar{v}_i+ \phi_1U_1 \cdot (\bar{b}_i-\bar{x}_i) + \phi_2 U_2 \cdot (\bar{c}_i-\bar{x}_i) $$
$$\bar{b}_i' = 
\begin{cases} 
\text{$\bar{x}_i'$ if } f(\bar{x}_i') < f(\bar{b}_i) \\
\text{$\bar{b}_i$ otherwise}
\end{cases}$$

where $w$ and $\phi_i$ are the weights and $U_1$ and $U_2$ are randomizer matrices and $\bar{c}$ denotes the populations global best.


## Individual and Social Factors in PSO

The velocity update equation in PSO is given by:
$$\bar{v}_i'= w \cdot \bar{v}_i+ \phi_1U_1 \cdot (\bar{b}_i-\bar{x}_i) + \phi_2 U_2 \cdot (\bar{c}_i-\bar{x}_i) $$
Here, the term $\phi_1U_1 \cdot (\bar{b}_i-\bar{x}_i)$ represents the individual component and $\phi_2 U_2 \cdot (\bar{c}_i-\bar{x}_i)$ represents the social component.

The value of $w$ can control exploration and exploitation. Specifically:
- For $w > 1$: Velocities increase over time and the swarm diverges.
- For $0 < w < 1$: The swarm converges.

## PSO: Example Moving Target
![[PSO_moving_target_ex_img.png]]
In a moving target scenario, the optimum moves randomly through the search space. Particles do not know the position of the optimum but do know which particle is closest and are attracted to that one. This requires a low $w$ value, and personal best ($b$) is zero.
