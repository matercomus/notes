# Indirect Constraint Handling

Indirect constraint handling is always needed when solving Constraint Satisfaction Problems (CSPs) because a CSP does not have an objective function $f$ in itself. For all constraints when using a CSP to FOP transformation, and for some constraints when using a CSP to COP transformation, those that get transformed into an objective are handled indirectly. 

Some general options for indirect constraint handling include:

1. **Penalty for violated constraints**: $f(\bar{s})=\sum_{i=1}^{m}{w_i \cdot x(\bar{s},c_i)}$, where 
$$x(\bar{s},c_i)= \begin{cases} 
1 & \text{if } \bar{s} \text{ violates } c_i \\
0 &  \text{otherwise} \\
\end{cases}$$
2. **Penalty for wrongly instantiated variables**: $f(\bar{s})=\sum_{j=1}^{m}{w_j \cdot x(\bar{s},c^j)}$, where 
$$x(\bar{s},c^j)= \begin{cases} 
1 & \text{if } \bar{s} \text{ violates at least one } c \in c^j \\
0 &  \text{otherwise} \\
\end{cases}$$
3. **Estimating distance/cost to feasible solution**: $f(\bar{s})=\sum_{i=1}^{m}{w_i \cdot d(\bar{s},c_i)}$, where 
$$d(\bar{s},c_i)= \begin{cases} 
1 & \text{if } \bar{s} \text{ violates } c_i \\
0 &  \text{otherwise} \\
\end{cases}$$

For each $\forall \bar{s}\in S: \phi(\bar{s}) \implies f(\bar{s})=0$

Notation:
- $c_i$: Constraints, where $i = \{1, … , m\}$.
- $v_j$: Variables, where $j = \{1, … , n\}$.
- $C_j$: The set of constraints involving variable $v_j$.
- $S_c = \{z \in D_{j1} \times … \times D_{jk} | c(z) = true\}$: This is the projection of $c$, if $v_{j1}, … , v_{jk}$ are the variables of $c$.
- $d(s, S_c) := min\{d(s, z) | z \in 2 S_c\}$: This is the distance of $s \in S$ from $S_c$ (where $s$ is projected to).

## Special Case: Graph Coloring Example
- Option *a* counts the wrong edges.
- Option *b* counts the wrong nodes.
- Option *c* counts the wrong edges if we take the number of necessary corrections (recolorings) as distance.

## Pros and Cons of Indirect Constraint Handling
**Pros**:
- Conceptually simple, transparent.
- Problem independent.
- Reduces problem to 'simple' optimization.
- Allows user to express preferences by different weights for different violations (weight per constraint or per variable).
- Allows EA to tune fitness function by modifying weights during the search.

**Cons**:
- Loss of info by packing everything in a single number.
- Said not to work well for sparse problems.
