# Constraint Satisfaction Problems (CSP)

## Definition
A Constraint Satisfaction Problem is defined as $<S, •, \phi>$ where:
- $S$ is a free search space.
- $\phi$ is a formula (Boolean function on $S$).

$\phi$ is the feasibility condition and $S_\phi = \set{s \in S | \phi(s) = true}$ is the feasible search space. The solution of a CSP is $s \in S$ such that $\phi(s) = true$ (i.e., $s$ is feasible).

## Constraints
$\phi$ is typically given by a set (conjunction) of constraints:
- $c_i = c_i(x_{j1}, … , x_{jni})$, where $n_i$ is the arity of $c_i$.
- $c_i \subseteq D_{j1} \times … \times D_{jni}$ is also a common notation.

**Facts:**
- The general CSP is **NP-complete.**
- Every CSP is equivalent with a binary CSP, where all $n_i = 2$.
- **Constraint density** and **constraint tightness** are parameters that determine **how hard** an instance is.


## Example: Graph 3-Coloring Problem
![[3_graph_coloring_problem_img.png]]

The Graph 3-coloring problem is a classic example of a Constraint Satisfaction Problem (CSP). The goal is to color the nodes of a graph in such a way that no two adjacent nodes share the same color. Here's a more detailed explanation:

- **Graph**: A graph $G$ is defined as a pair $(N, E)$, where $N$ is a set of nodes and $E$ is a set of edges. Each edge in $E$ is a pair of nodes in $N$. The notation $E \subseteq N \times N$ means that each edge is a pair of nodes, and $|N| = n$ means that the number of nodes in the graph is $n$.

- **Search Space**: The search space $S$ is defined as $D^n$, where $D = {1, 2, 3}$ represents the three colors that can be assigned to each node. So an element of the search space is an assignment of one of the three colors to each node in the graph.

- **Feasibility Condition**: The feasibility condition $\Phi(s)$ checks whether a given color assignment $s$ is valid. It's defined as $\bigwedge_{e\in E} c_e(s)$, which means "for all edges $e$ in $E$, check the constraint $c_e(s)$". The constraint $c_e(s)$ is true if and only if for an edge $e = (k, l)$, the colors assigned to nodes $k$ and $l$ are different, i.e., $s_k \neq s_l$. This ensures that no two adjacent nodes share the same color.
