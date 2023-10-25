# Constrained Optimization Problems (COP)

A Constrained Optimization Problem is defined as $<S, f, \phi>$ where:
- $S$ is a free search space.
- $f$ is a real-valued objective function on $S$.
- $\phi$ is a formula (Boolean function on $S$).

The solution of a COP is $s \in S_\phi$ such that $f(s)$ is optimal in $S_\phi$.

## Example: Travelling Salesman Problem
![[TSP_map_img.png]]

Consider a set of cities $C = \set{city_1, … , city_n}$. 
The search space is defined as $S = C^n$. 
The feasibility condition is defined as $$\Phi(s) = true \Leftrightarrow \forall i, j \in \{1, … , n\} i \neq j \Rightarrow s_i \neq s_j$$
The objective function is defined as $$f(s)= \sum_{i=1}^{n}{dist(S_i,S_{i+1})}$$ where $S_{n+1} := S_1$

