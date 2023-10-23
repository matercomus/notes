# Neuroevolution

Neuroevolution is a form of artificial intelligence that uses evolutionary algorithms to generate artificial neural networks, parameters, topology and rules. It is most commonly applied in situations where the task is complex and no explicit fitness function exists.

## Applications
Neuroevolution is often used for control tasks and generative challenges. It can also be applied to prediction and classification problems.

*Image placeholder here for future reference*

## Main Variants
1. **Evolving only the weights** of a network with fixed topology.
2. **Evolving the topology** of the network.
3. **Evolving the activation functions** of the network.

## Pros and Cons
**Pros**:
- Can be used for supervised, unsupervised, and semi-supervised learning tasks.
- Can avoid local optima by explicit diversity maintenance methods (because EAs are population based).
- Allows for combining multiple criteria as objective.
- Can generate creative and interesting solutions, instead of just “perfect solutions”.

**Cons**:
- Computationally expensive in comparison to learning methods (a whole population of solutions to be tested).

## Simple Neuroevolution
In simple neuroevolution, only the weights of a network with a fixed topology are evolved. This transforms the neural network learning problem into a vector optimization problem.

*Image placeholder here for future reference*

## Advanced methods
- Make the topology also evolvable: 
        Topology and Weight Evolving Artificial Neural Network (TWEANN) 
- And even the activation functions

- [[NEAT]]: NEUROEVOLUTION OF AUGMENTING TOPOLOGIES
- [[CPPNS]]: COMPOSITIONAL PATTERN PRODUCING NETWORKS 
- [[HYPERNEAT]]

## Types of Encoding
![[Neuroev_encoding_types_img.png]]


