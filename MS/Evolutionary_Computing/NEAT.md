# NEAT: NeuroEvolution of Augmenting Topologies

NEAT is a method for evolving artificial neural networks with a genetic algorithm. It evolves not only the weights of the network but also the topology, starting from minimal structure and allowing complexity to increase over generations.

## Main Premises
![[Minimal_topo_img.png]]
- Networks bigger than necessary are expensive to optimize. Therefore, NEAT aims for **minimality**, keeping the topology complexity as minimal as possible.
- NEAT protects innovation through **speciation**, giving innovations a chance to show their potential.

## Reproduction
![[Aug_topo_img.png]]
NEAT uses unique historical markers to identify genes, which helps in aligning two genomes for crossover. 
![[Historical_markesrs_i_img.png]]
Matching genes are inherited randomly, while disjoint genes and excess genes are inherited from the more fit parent.
![[Aug_topo_2_img.png]]
## Mutation
![[Mut_topo_img.png]]
Different types of mutation can happen, each with its own probability. Multiple types could happen in the same mutation. The types of mutation include:
- Add node
- Remove node
- Add connection
- Remove connection
- Mutate weight

## Speciation
Innovations can be disruptive: a single extra node could make the network behave very differently. To protect innovation and maintain diversity, NEAT uses **speciation**. Individuals compete only within their species, and individuals within a species are similar.

## Full Cycle
The full cycle of NEAT includes assigning individuals to species, fitness sharing, and reproduction/selection.
![[Neat_graph_img.png]]

## Compatibility Distance

![[Compat_dist_img.png]]
## Pros and Cons
**Pros**:
- Can be used for supervised, unsupervised, and semi-supervised learning tasks.
- Can avoid local optima by explicit diversity maintenance methods (because EAs are population based).
- Allows user to express preferences by different weights for different violations (weight per constraint or per variable).
- Can generate creative and interesting solutions, instead of just “perfect solutions”.

**Cons**:
- Computationally expensive in comparison to learning methods (a whole population of solutions to be tested).
