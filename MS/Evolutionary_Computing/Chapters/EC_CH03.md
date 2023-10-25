## Chapter 3 - What is an Evolutionary Algorithm?

#### Common model of evolutionary processes

- Population of individuals
- Individuals have a fitness
- Reproduction/Variation operators
	- Mutation
	- Recombination (crossover)
- Selection towards higher fitness
	- "Survival of the fittest"
	- "mating of the fittest"
- The fitness of the population increases over time

#### Two pillars of evolution

| Increasing population diversity by variation | Decreasing population diversity by selection |
| -------------------------------------------- | -------------------------------------------- |
| - mutation                                   | - of parents                                 |
| - recombination                              | - of survivors                               |
| Push towards novelty                         | Push towards quality                         |

#### What is an Evolutionary Algorithm?

- [[Scheme of an EA]]
- Main EA components:
	- [[Representation]]
	- [[Evaluation and Fitness Function]]
	- [[Population]]
	- [[Selection]]
	- [[Variation Operators]]
	- [[Mutation]]
	- [[Recombination]]
	- [[Initialization and Termination]]
- [[Different EA Types]]
- [[Typical EA Behavior]]
- [[EAs in Context]]
- [[EAs as Problem Solvers]]
- [[EC and Global Optimization]]
#### [[The 8-Queens problem]] #TODO 

#### Important Points:

- There are different diagrams to represent an EA scheme

- Variation operators push towards novelty and selection operators push towards quality
- Variation operators need to match the representation, selection operators are independent from the representation (hence, from the problem at hand)

- [[Selection operators]] act on the population level and variation operators on the individual level