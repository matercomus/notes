
## Local Search Acting on Offspring

### Lifetime Learning
Local search can be viewed as a sort of "lifetime learning". Lots of early research was done using Evolutionary Algorithms (EAs) to evolve the structure of Artificial Neural Networks and then Back-propagation to learn connection weights.

### Endgame Speed-up
Local search is often used to speed-up the "endgame" of an EA by making the search in the vicinity of good solutions more systematic than mutation alone.

## Local Search and Graphs: Local Search

### Definition
![[Local_search_neighbourhod_img.png]]
**Local search** is defined by a combination of neighbourhood and pivot rule. The neighbourhood N(x) of point x is the set of points that can be reached from x with one application of a move operator (this is an "operational" definition). 

For example, bit flipping search on binary problems. 
The **pivot rule** is the condition for stopping neighbourhood search, e.g., greedy ascent.

## Local Search and Graphs: Landscapes & Graphs

### Representation and Operator
The combination of representation and operator defines a graph G(V,E) on the search space (useful for analysis), where V, the set of vertices, is the set of all points that can be represented (the potential solutions), and E, the set of edges, is the possible transitions that can arise from a single application of the search operator. Note that the edges in E can have weights attached to them, and that they need not be symmetrical.

#### 3-Dimensional Binary Problem

Consider a 3-dimensional binary problem with the following vertices:
$V = \{a,b,c,d,e,f,g,h\}$

For example, `b = (0,0,0)`.

The search is conducted by flipping each bit in turn. This results in the following edge sets:

- $E_1 = \{ ab, ad, ae, bc, bf, cd, cg, dh, fg, fe, gh, eh\}$ (1 bit-flip)
- $E_2 = \{ac,bd,af,be,dg,ch,fh,ge,ah,de,bg,cf\}$ (2 bit-flips)
- $E_3 = \{ag,bh,ce,df\}$ (3 bit-flips)

These edge sets are symmetrical and all values are equally likely. Bit flipping mutation with probability $p$ per bit implies weights on these edges.


## Local Search and Graphs: Graphs

The degree of a graph is the maximum number of edges coming into/out of a single point - the size of the biggest neighbourhood. For example:

- Single bit changing search: degree is L (length of the bit vector)
- Bit-wise mutation on binary: degree is 2L -1
- 2-opt: degree is $O(N^2)$

Local Search algorithms look at points in the neighbourhood of a solution, so complexity is related to the degree of the graph.

## Local Search and Graphs: Pivot Rules

The overall strategy determines whether the neighbourhood is searched randomly, systematically or exhaustively. The stopping condition can vary:

- Greedy Ascent: stop as soon as a fitter neighbor is found
- Steepest Ascent: stop after the whole set of neighbours examined and choose the best

There's no one best answer in general, but some are quicker than others to run.

## Variations of Local Search

Variants can be defined by, for instance:

- **Where does the search happen, in representation space (genotype space) or solution space (phenotype space)?** The search can happen in either space depending on the specific implementation of the algorithm. For example, in a genetic algorithm solving the 8 queens problem, the genotype could be a string representing the positions of the queens, while the phenotype would be the actual board configuration. The search could operate on the string representations (genotype space) or directly on the board configurations (phenotype space).

- **How many iterations of the local search are done?** The number of iterations can vary based on the specific problem and algorithm. Some algorithms may perform a fixed number of iterations, while others may continue until a certain condition is met, such as a time limit or a satisfactory solution being found.

- **Is local search applied to the whole population? Or just the best? Or just the worst? Or at random?** This also depends on the specific algorithm and problem. Some algorithms may apply local search to every individual in the population, while others may only apply it to a subset, such as the best or worst individuals, or a random selection.

The advantages of searching in phenotype space include potentially more meaningful mutations and recombination, and easier incorporation of problem-specific knowledge. The disadvantages include potentially higher computational cost and complexity.


# Two Models of Lifetime Adaptation

## Lamarckian
Lamarckian theory, also known as Lamarckism, proposes that traits acquired by an individual during its lifetime can be transmitted to its offspring. In the context of Evolutionary Algorithms (EAs), this is implemented by replacing an individual with a fitter neighbor, thus using another genotype.
#### Explanation
Lamarckian evolution, named after the French biologist Jean-Baptiste Lamarck, is a method in evolutionary computation where an individual’s traits change during its lifetime due to learning or adaptation, and these changes are passed on to its offspring. In other words, the genotype of an individual is directly altered based on its experiences or adaptations during its lifetime.

In the context of Evolutionary Algorithms (EAs), this is implemented by replacing an individual with a fitter neighbour, thus using another genotype. This means that if an individual finds a better solution through local search (or any other learning mechanism), this improved solution replaces the original one in the population and can be used for further genetic operations like crossover and mutation.

The advantage of this approach is that it can accelerate the evolutionary process because beneficial traits are directly incorporated into the genetic material and thus can be inherited by future generations. This can lead to a faster convergence towards optimal or near-optimal solutions.

However, there are also potential downsides. One risk is that Lamarckian evolution can reduce the diversity of the population too quickly, leading to premature convergence on suboptimal solutions. This happens when the population becomes dominated by individuals that have acquired similar beneficial traits, leaving less room for exploration of other potentially fruitful areas of the search space.

It’s worth noting that while Lamarckian evolution is not generally accepted in biological evolution, it can be a powerful tool in artificial evolution (such as EAs) where the goal is often to find good solutions as quickly as possible.

## Baldwinian
Baldwinian theory, on the other hand, suggests that traits acquired by an individual cannot be transmitted to its offspring. In EAs, this is implemented by allowing an individual to receive the fitness of a fitter neighbor but keeping its own genotype.
#### Explanation
The practice of giving an individual the fitness of another without changing its genotype is often used in Baldwinian evolutionary strategies. The idea is to allow individuals to “learn” or adapt during their lifetime and use this learned knowledge to guide the search process, without directly altering the genetic material that is passed on to the next generation.

This approach can be beneficial in certain scenarios. For instance, it allows the population to explore the fitness landscape more thoroughly. Since the genotype doesn’t change, the population maintains its diversity, which can be crucial for exploring new and potentially better solutions. At the same time, by adopting the fitness values of more successful individuals, less fit individuals can “learn” from them and guide the search towards promising regions of the solution space.

It’s important to note that whether this strategy is effective or not can depend on the specific problem at hand and the characteristics of the fitness landscape. In some cases, a Lamarckian approach, where both the fitness and the genotype of an individual are changed, might be more effective. It’s all about finding the right balance between exploration (searching new solutions) and exploitation (refining current solutions).
## Baldwin vs. Lamarck
There has been a lot of research on this topic. The central dogma of genetics is that traits acquired during an organism's lifetime cannot be written back into its gametes. However, the field of epigenetics provides extra nuance to this understanding. 

In Memetic Algorithms (MAs), we are not constrained by biological realities so we can implement Lamarckism. Recent work in evolutionary robotics suggests that Lamarckism may be more effective!
