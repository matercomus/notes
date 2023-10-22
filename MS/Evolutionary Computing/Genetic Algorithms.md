# Genetic Algorithms: Quick Overview

Genetic Algorithms were developed in the USA in the 1960s by early pioneers such as J. Holland, K. DeJong, and D. Goldberg. They are typically applied to discrete function optimization and benchmark straightforward problems with binary representation.

## Key Features

- **Speed**: Genetic Algorithms are not typically known for their speed.
- **Variants**: There are many variants of the original Genetic Algorithm, including those that incorporate elitism and Stochastic Universal Sampling (SUS).
- **Theoretical Modeling**: Genetic Algorithms are often modeled by theorists.
- **Simple Genetic Algorithm (SGA)**: Holland's original GA is now known as the Simple Genetic Algorithm (SGA).
- **Variations**: Other GAs use different representations, mutations, crossovers, and selection mechanisms.

### SGA technical summary tableau

| Representation     | Bit-strings                          |
| ------------------ | ------------------------------------ |
| Recombination      | 1-poit crossover                     |
| Mutation           | Bit flip                             |
| Parent Selection   | Fitness proportional -roulette wheel |
| Survivor Selection | Generational                                     |

### Reproduction Cycle

The reproduction cycle of a Simple Genetic Algorithm (SGA) involves the following steps:

1. **Select Parents for the Mating Pool**: The size of the mating pool is equal to the population size.
2. **Shuffle the Mating Pool**: This ensures a random selection of parents for crossover.
3. **Apply Crossover**: For each consecutive pair in the shuffled mating pool, apply crossover with probability $p_c$. If crossover does not occur, simply copy the parents.
4. **Apply Mutation**: For each offspring resulting from crossover, apply mutation. This is typically done as a bit-flip mutation with probability $p_m$, independently for each bit.
5. **Replace Population**: Replace the entire population with the resulting offspring.

## GA Example After Goldberg '89

Consider a simple problem: maximize $x^2$ over $\{0,1,\ldots,31\}$. The GA approach to this problem would involve:

- **Representation**: Binary code (e.g., 01101 $\leftrightarrow$ 13)
- **Population Size**: 4
- **Operators**: 1-point crossover, bitwise mutation
- **Selection Mechanism**: Roulette wheel selection
- **Initialization**: Random

We can show one generational cycle done by hand to illustrate how these steps work in practice.

#### $x^2$ Example: Selection
![[SGA_selection_example_table_img.png]]
#### $x^2$ Example: Crossover
![[SGA_corss_example_table_img.png]]
#### $x^2$ Example: Mutation
![[SGA_mut_example_table_img.png]]

## The Simple Genetic Algorithm (SGA)

The Simple Genetic Algorithm (SGA) has been the subject of many early studies and is still often used as a benchmark for novel Genetic Algorithms (GAs). However, it shows many shortcomings:

- **Representation**: The representation in SGA is often too restrictive.
- **Operators**: Mutation and crossover operators are only applicable for bit-string and integer representations.
- **Selection Mechanism**: The selection mechanism in SGA is sensitive for converging populations with close fitness values.
- **Population Model**: The generational population model (step 5 in SGA reproduction cycle) can be improved with explicit survivor selection.

## Genetic Algorithms: Summary

Genetic Algorithms are good for combinatorial optimization and constraint satisfaction. There are many different variants of GAs, offering lots of design choices. GAs have a large academic fanbase. However, the name GA is often (ab)used for a different Evolutionary Algorithm (EA).