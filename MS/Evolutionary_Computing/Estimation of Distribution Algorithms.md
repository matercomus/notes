# Estimation of Distribution Algorithms (EDA)

EDAs are a type of evolutionary algorithm that aim to overcome the limitations of traditional EAs by learning about the fitness landscape.

## Overview
1. **Create initial population randomly**: Start with a set of randomly generated solutions.
2. **Calculate fitness of each candidate**: Evaluate the quality or fitness of each solution in the population.
3. **Select a subpopulation**: Choose a subset of the best candidates from the current population.
4. **Select a model to fit a probability distribution over the candidates**: Use statistical methods to estimate the distribution of solutions in the selected subset.
5. **Sample new population from this estimated distribution**: Generate a new population of solutions by sampling from the estimated distribution.
6. **Back to step 2**: Repeat the process until a satisfactory solution is found or a stopping condition is met.

## Model-assisted EAs
In addition to using a model in the reproduction step (as in EDAs), some EAs also use a model in the fitness evaluation step. The rationale behind this is that fitness evaluation is often the most time-consuming step in an EA, and sampling from a model is usually much faster. Therefore, the overhead of building a model could pay off. In this approach, x% of fitness evaluations are real, and 100-x% are model-based.
