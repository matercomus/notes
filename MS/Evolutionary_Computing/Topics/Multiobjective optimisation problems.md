# Multi-Objective Problems (MOPs)

A wide range of problems can be categorized by the presence of $n$ possibly conflicting objectives. Examples include:

- Buying a car: speed vs. price vs. reliability
- Engineering design: lightness vs. strength

The two main problems are:
1. Finding a set of good solutions
2. Choosing the best solution for a particular application

## Example: Buying a Car

![[MOP_car_img.png]]
![[Decision_objective_space_img.png]]
## Comparing Solutions
![[Pareto_space_1_img.png]]
The optimization task is to minimize both $f1$ and $f2$. Then:

- $a$ is better than $b$
- $a$ is worse than $e$
- $a$ is better than $c$ (they are equal on $f1$, $a$ wins on $f2$)
- $a$ and $d$ are incomparable ($a$ wins on $f1$, $d$ wins on $f2$)

## Dominance Relation
![[Pareto_space_2_img.png]]
Solution $x$ dominates solution $y$, denoted as ($x \succeq y$), if:

- $x$ is better than $y$ in at least one objective,
- $x$ is not worse than $y$ in all other objectives

# Pareto Optimality

A solution $x$ is non-dominated in a set of solutions $Q$ if no solution from $Q$ dominates $x$ (has no "master" in $Q$). This concept leads to the following definitions:

- **Pareto-optimal set**: A set of non-dominated solutions in the solution space ($Q$ = set of all feasible solutions). Its members are the Pareto-optimal solutions.

![[Pareto_front_1_img.png]]

- **Pareto-optimal front**: An image of the Pareto-optimal set in the objective space.

![[Pareto_front_2_img.png]]
## Example: Beam Design Problem

The goal is to minimize weight and deflection of a beam (Deb, 2001).

![[Beam_deflection_img.png]]

The decision (variable) space consists of length $l$ and diameter $d$. The objective space consists of weight and deflection.

### Formal definition

- Minimize (beam weight)
$$f_1(d,l)=\rho\frac{\pi d^2}{4}l$$
- Minimize (beam deflection)
$$f_2(d,l)=\delta =\frac{64pl^3}{3E\pi d^4}l$$
$0.01m \leq d \leq 0.05m$
$0.2m \leq l \leq 1.0m$

- Subject to (maximum stress)
$$\sigma_{max}=\frac{32pl}{d^3}\leq S_y$$
$\delta \leq \delta_{max}$
$\rho=7800 kg/m^3$, $P= 2kN$
$E=207 GPa$
where $S_y=300 MPa$, $\delta_{max}=0.005m$

### Feasable solutions

![[Pareto_5_img.png]]

### Goal: find non-dominated solutions

![[Pareto_4_img.png]]


### Goal of Multiobjective Optimisers
![[Pareto_3_img.png]]
Find a set of non-dominated solutions (approximation set) following the criteria of:
- Convergence (get as close as possible to the Pareto-optimal front),
- Diversity (spread, distribution)


### Single vs. multiobjective optimisation
![[Single_vs_multi_opt_table_img.png]]


