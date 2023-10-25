- One of the earliest representations
- Genotype consists of a string of binary digits
![[Binary_rep_mapping_img.png]]

### Mutation

![[Binary_mut1_img.png]]
- Alter each gene independently with a probability $p_m$
- $p_m$ is called the mutation rate
- Typically between 1/pop_size and 1/ chromosome_length
- Mutation can cause variable effect (standard vs. Gray coding)

### Crossover
#### 1-Point Crossover
![[One_point_cross_img.png]]
- Choose a random point on the two parents
- Split parents at this crossover point
- Create children by exchanging tails
- $P_c$ typically in range (0.6, 0.9)


#### Alternative Crossovers
- Why do we need other crossover(s)?
- Performance with 1-point crossover depends on the order that variables occur in the representation (**Positional Bias**)
	- More likely to keep together genes that are near each other
	- Can never keep together genes from opposite ends of string
	- Can be exploited if we know about the structure of our problem, but this is not usually the case

##### N-point Crossover
![[N_point_cross_img.png]]
- Choose n random crossover points
- Split along those points
- Glue parts, alternating between parents
- Generalization of 1-point (still some **positional bias**)

##### Uniform Crossover
![[Uniform_cross_img.png]]
- Assign 'heads' to one parent, 'tails' to the other
- Flip a coin for each gene of the first child
- Make an inverse copy of the gene for the second child
- Inheritance is independent of position


##### Crossover or Mutation?
- Decade long debate: which one is better / necessary / main-background 
- Answer (at least, rather wide agreement):
	- it depends on the problem, but
	- in general, it is good to have both
	- both have another role
	- there are mutation-only-EAs (some [[Evolution Strategies]]), as well as xover-only-EAs (some [[Genetic Programming]])

**Exploration**: Discovering promising areas in the search space, i.e. gaining information on the problem
**Exploitation**: Optimizing within a promising area, i.e. using information

There is co-operation AND competition between them
- **Crossover** 
	- is **explorative**, it makes a big jump to an area somewhere “in between” two (parent) areas.
	- can **combine information** from two parents
	- does not change the allele frequencies of the population
- **Mutation** 
	- is **exploitative**, creates random small variations, thereby staying near (in the area of) the parent.
	- can **introduce new information** (new alleles, “fresh blood”)
	- To hit the optimum you often need a “lucky” mutation