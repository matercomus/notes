Trees are a universal form, e.g. consider:
![[Tree_rep_math_img.png]]

![[Tree_rep_logic_img.png]]

![[Tree_rep_program_img.png]]

- In [[Genetic Algorithms]], [[Evolutionary Strategies]], [[Evolutionary Programming]] chromosomes are linear structures (bit strings, integer string, real-valued vectors, permutations)
- Tree shaped chromosomes are non-linear structures
- In GA, ES, EP the size of the chromosomes is fixed
- Trees in GP may vary in depth and width 
### Symbolic Expressions

Symbolic expressions can be defined by the following:

- **Terminal set** $T$
- **Function set** $F$ (with the arities of function symbols)

Adopting the following general recursive definition:

1. Every $t \in T$ is a correct expression
2. $f(e_1, \ldots, e_n)$ is a correct expression if $f \in F$, $\text{arity}(f)=n$ and $e_1, \ldots, e_n$ are correct expressions 
3. There are no other forms of correct expressions

In general, expressions in GP are not typed (closure property: any $f \in F$ can take any $g \in F$ as argument).


### Mutation
- Most common mutation: replace randomly chosen subtree by randomly generated tree
![[Tree_mut_img.png]]
#### Mutation Parameters
Mutation has two parameters:
- Probability $p_m$ to choose mutation 
- Probability to chose an internal point as the root of the subtree to be replaced

Remarkably, $p_m$ is advised to be 0 (Koza’92) or very small, like 0.05 (Banzhaf et al. ’98). The size of the child can exceed the size of the parent.


### Recombination
Most common recombination: exchange two randomly chosen subtrees among the parents.
![[Tree_recomb_img.png]]
#### Recombination Parameters
Recombination has two parameters:
- Probability $p_c$ to choose recombination 
- Probability to chose an internal point within each parent as crossover point

The size of offspring can exceed that of the parents.
