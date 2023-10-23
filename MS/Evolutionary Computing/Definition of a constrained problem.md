# Constrained Problems and Search

## Constrained Problem
Consider the Travelling Salesman Problem for $n$ cities, $C = \set{city_1, … , city_n}$. The notion of a 'constrained problem' depends on what we take as the search space. For example:
1. If we define the search space as $S = Cn$, then we need a constraint requiring uniqueness of each city in an element of $S$.
2. If `S = {permutations of C}`, then we need no additional constraint.

## Constrained Search vs Free Search
Even in the space `S = {permutations of C}` we cannot perform free search. 
- **Free Search:** standard mutation and crossover preserve membership of $S$.
	- $mut(x) \in S$ and $cross(x,y) \in S$
 
The notion of 'free search' depends on what we take as standard mutation and crossover.

- **Standard Mutation** ($mut$)
	If for all $<x_1, … , x_n>$, if $mut(<x_1, … , x_n>) = <x_1', … , x_n'>$,
	then $x_i' \in domain(i)$.
- **Standard Crossover ($cross$)**
	If for all $<x_1, … , x_n>$, $<y_1, … , y_n>$,
	If $cross(<x_1, … , x_n>, <y_1, … , y_n>) = <z_1, … , z_n>$, then:
	- $z_i \in \set{xi, yi}$ (discrete case)
	- $z_i \in [xi, yi]$ (continuous case)

These are very light (non-restrictive) conditions.

## Free Search Space
A free search space is defined as $S = D_1 \times … \times D_n$ with **one assumption** on $D_i$: 
- ==If it is continuous, it is convex. ==
- The restriction $s_i \in D_i$ is not a constraint, it is the definition of the domain of the $i$-th variable. 
- Membership of $S$ is coordinate-wise, hence a free search space allows free search.

A problem can be defined through:
- An objective function (to be optimized)
- Constraints (to be satisfied)

## Problem Categorization Schemes
Recall the 3 schemes discussed in Chapter 1:
- Optimization – modeling – simulation scheme (where is the ?)
- FOP – COP – CSP scheme (2 x 2 matrix)
- NP scheme (based on solver properties)

### Optimization vs. Constraint Satisfaction
==Constrain**t** vs. Constrain**ed**==

|                  | Objective Function: Yes | Objective Function: No |
| ---------------- | ----------------------- | ---------------------- |
| Constraints: Yes | COP                     | CSP                    |
| Constraints: No  | FOP                     | NP                     |

- **FOP**: [[Free Optimization Problem]]
- **CSP**: [[Constraint Satisfaction Problem]]
- **COP**: [[Constrained Optimisation Problem]]
- **NP**: No Problem


