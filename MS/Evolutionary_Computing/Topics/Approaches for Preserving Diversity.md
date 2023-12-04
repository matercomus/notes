# Explicit vs Implicit Approaches

## Explicit Approaches

Explicit approaches make similar individuals compete for resources (e.g., resource is fitness, fight for better fitness) or make similar individuals compete with each other for survival.

### Fitness Sharing

Fitness sharing is an explicit approach that restricts the number of individuals within a given niche by "sharing" their fitness, so as to allocate individuals to niches in proportion to the niche fitness. This means high fitness region has many individuals, while low fitness region has few individuals.

The "geometrical" size of the niche $\sigma_{\text{share}}$ needs to be set by distance in either genotype or phenotype space (thus: $\sigma_{\text{share}}$ is NOT the number of individuals in that niche).

The EA is run as normal but after each generation set $f(i)$ to $f'(i)$ where:

- $f(i)$: The fitness of the $i$-th individual.
- $\mu$: The total number of individuals.
- $d(i,j)$: The distance between the $i$-th and $j$-th individual.
- $\sigma$: The size of the niche.
$$f'(i)=\frac{f(i)}{\sum_{j=1}^{\mu} sh(d(i,j))}$$
and
$$sh(d)= \begin{cases} 
1-d/\sigma & \text{if } d \leq \sigma \\
0 & \text{otherwise}
\end{cases}$$

Note: if we used $sh(d) = 1$ instead of $sh(d) = 1 – d/\sigma_{\text{share}}$ then the sum that reduces the fitness would simply count the number of neighbours, i.e., individuals closer than $\sigma_{\text{share}}$. This creates an advantage of being alone in the neighbourhood. Using $1 – d/ \sigma_{\text{share}}$ instead of $1$ implies that we count distant neighbours less than close neighbours.

#### Fitness Sharing Calculation Example
In this example, we have a [[Population]] of individuals with the following fitness values:
![[Fit_sharing_landscape_img.png]]
- $f(2) = 2$
- $f(3) = 2.5$
- $f(4) = 3$
- $f(10) = 4$
- $f(12) = 5$

We also have a niche size $\sigma = 3$. 

For individual 2, it has two neighbors (individuals 3 and 4) within the niche size. So, its shared fitness is calculated as:
$$f'(2) = \frac{2}{1 + 1/3 + 2/3} = 1$$
For individual 10, it has one neighbor (individual 12) within the niche size. So, its shared fitness is calculated as:
$$f'(10) = \frac{4}{1 + 1/3} = 3$$
So, even though individual 10 is twice as good as individual 2 in terms of raw fitness, after applying fitness sharing, individual 10 is only three times as good as individual 2.


### Crowding

Crowding is an explicit approach that attempts to distribute individuals evenly amongst niches. It relies on the assumption that offspring will be close to parents and uses a distance metric in either phenotype or genotype space.
##### Key Concepts
- **Parent-Offspring Tournaments**: Take 2 parents and their 2 offspring and set up parent vs. child tournaments such that the inter-tournament distances are minimal. That is, number the two parents ($p_1$ and $p_2$) and the two offspring ($o_1$ and $o_2$) such that:
$$d(p_1,o_1) + d(p_2,o_2) < d(p_1,o_2) + d(p_2,o_1)$$
where $d(x,y)$ represents the distance between individuals $x$ and $y$. Then, let $o_1$ compete with $p_1$ and $o_2$ compete with $p_2$.

#### Crowding example calculation
Consider an example with four individuals: two parents and two offspring. We'll represent each individual as a point in a 2D space for simplicity. Let's say we have:

- Parent 1 ($p_1$) at coordinates (1, 1)
- Parent 2 ($p_2$) at coordinates (3, 3)
- Offspring 1 ($o_1$) at coordinates (2, 2)
- Offspring 2 ($o_2$) at coordinates (4, 4)

We can calculate the Euclidean distance between two points $(x_1, y_1)$ and $(x_2, y_2)$ using the formula:
$$d = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$$
Using this formula, we find that:
- The distance between $p_1$ and $o_1$ is $\sqrt{(2-1)^2 + (2-1)^2} = \sqrt{2}$
- The distance between $p_2$ and $o_2$ is $\sqrt{(4-3)^2 + (4-3)^2} = \sqrt{2}$

So, $d(p_1,o_1) + d(p_2,o_2) = 2\sqrt{2}$.

On the other hand:
- The distance between $p_1$ and $o_2$ is $\sqrt{(4-1)^2 + (4-1)^2} = 3\sqrt{2}$
- The distance between $p_2$ and $o_1$ is $\sqrt{(3-2)^2 + (3-2)^2} = \sqrt{2}$

So, $d(p_1,o_2) + d(p_2,o_1) = 4\sqrt{2}$.

Since $d(p_1,o_1) + d(p_2,o_2) < d(p_1,o_2) + d(p_2,o_1)$, we let $o_1$ compete with $p_1$ and $o_2$ compete with $p_2$, as per the crowding method.


### Crowding vs Fitness Sharing
![[Crowding_vs_fit_share_plot_img.png]]
Observe the number of individuals per niche
## Implicit Approaches

Implicit approaches impose an equivalent of geographical separation or impose an equivalent of speciation.

### Automatic Speciation

Automatic speciation is a method used in genetic algorithms to maintain diversity in the population. It works by restricting mating to individuals that are similar in some way.
##### Key Concepts
- **Genotypic/Phenotypic Similarity**: One approach is to restrict mating to genotypically or phenotypically similar individuals. This means that individuals can only mate with others that have a similar genetic makeup or exhibit similar traits.

- **Tagging**: Another approach is to restrict mating to individuals that have the same (or very similar) tag. A tag is an extra bit (or bits) in the genotype that is initialized randomly and is subject to [[Recombination]] and [[Mutation]]. This allows for the formation of subpopulations within the overall population, each with its own unique tag.


### Island Model - Parallel EAs
![[Island_model_img.png]]
The Island Model is an implicit approach used in parallel Evolutionary Algorithms (EAs) to maintain diversity in the population. It works by running multiple populations in parallel and allowing periodic migration of individuals between these subpopulations.
#### Key Concepts
- **Multiple Populations**: Run multiple populations in parallel. Each population evolves independently for the most part, allowing for the exploration of different areas of the solution space.

- **Periodic Migration**: After a usually fixed number of generations – called an epoch – exchange individuals with neighbors. This allows for the sharing of potentially beneficial genetic material between populations.

- **Repeat Until Stopping Criteria Met**: The process of evolution within each population and migration between populations is repeated until some stopping criteria are met.

- **Inspiration from Parallel/Clustered Systems**: The Island Model is partially inspired by parallel and clustered systems, where different processors or nodes perform computations independently and periodically synchronize with each other.

#### Island Model: Parameters

The Island Model has several parameters that can be adjusted to optimize the performance of the parallel Evolutionary Algorithm (EA).

#### Key Parameters

- **Migration Frequency**: How often should individuals be exchanged? If done too quickly, all sub-populations may converge to the same solution. If done too slowly, time may be wasted. Most authors use a range of 25-150 generations. This can also be done adaptively, stopping each population when there's no improvement for X generations.

- **Number and Type of Migrants**: How many individuals, and which individuals, should be exchanged? Usually around 2-5, but this depends on the population size. Some results show that it's better to exchange randomly selected individuals than the best individuals. The "multi-culti" approach, which exchanges the most different ones, is even better.

- **Copied vs Moved**: Should the migrating individuals be copied or moved from their original population to the new one?

- **[[Variation Operators]]**: Variation operators can differ per sub-population or island. This allows each sub-population to explore the solution space in a slightly different way, potentially leading to greater overall diversity.


## Cellular EAs
![[Cellular_EAs_vis_img.png]]
Cellular Evolutionary Algorithms (EAs) are a type of implicit approach used to maintain diversity in the population. In Cellular EAs, each individual exists on a point on a grid (usually a rectangular toroid), and [[Selection]] (hence recombination) and replacement happen using the concept of a neighbourhood, also known as a [[deme]].

## Key Concepts

- **Grid Structure**: The population is structured as a grid, with each individual occupying a point on the grid. This leads to different parts of the grid searching different parts of the solution space.

- **Neighbourhoods/Demes**: Selection and replacement are based on the concept of a neighbourhood or deme. Good solutions can diffuse across the grid over a number of generations.

- **One Generation**: The equivalent of one generation in Cellular EAs involves the following steps:
    - Pick an individual in the population at random.
    - Pick one of its neighbours using roulette wheel selection or some other method.
    - Apply crossover to produce one child, then mutate the child to get the final offspring.
    - Replace the original individual if the offspring is fitter.
    - Repeat this process for each individual in the population.
