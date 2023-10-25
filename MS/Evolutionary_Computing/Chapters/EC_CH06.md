# Popular Evolutionary Algorithm Variants

## Historical EA variants
- [[Genetic Algorithms]] (GA)
- [[Evolution Strategies]] (ES)
- [[Evolutionary Programming]] (EP)
- [[Genetic Programming]] (GP)

## More recent variants
- [[Differential Evolution]] (DE)
- [[Particle Swarm Optimisation]] (PSO)
- [[Learning Classifier Systems]] (LCS)
- [[Estimation of Distribution Algorithms]] (EDA)

## Important Points

- There are several incarnations / dialects / variants of the generic EA scheme.
- The classic variants are: Genetic Algorithms (GA), Evolution Strategies (ES), Evolutionary Programming (EP), Genetic Programming (GP).
- Some of these have a primary application area:
	- GA: Discrete / combinatorial optimization
	- ES: Continuous optimization
	- GP: Machine learning, modeling
- Methods and tricks invented in one branch can often be applied in other ones.
- Some techniques, e.g., Particle Swarm Optimization (PSO), use non-evolutionary metaphors, but the algorithm follows the generic EA template.
- Beware of "novel" metaphors with bombastic names – these may be equivalent to existing variants!
- The specific type of EA is not important for applications.
- Best approach in practice:
	- Choose representation to fit the problem.
	- Choose variation operators to fit representation.