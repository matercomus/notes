# EC Approach for Multi-objective Optimization

## Main Rationale

Evolutionary Algorithms (EAs) are population-based methods, hence inherently well suited to return a set of trade-off solutions (approximation set) in a single run. This allows for both:

- The aggregation-based approach and
- The real multi-objective approach

## Advantages of EC Approach

- Population-based nature means EA can simultaneously search for a set of points approximating Pareto front
- No need to make guesses before or during the search about which trade-offs (weights) might be useful
- No assumptions needed about the shape of the Pareto front - can be convex / discontinuous, etc.

## Requirements of EC Approach

We need:

1. Appropriate method to define fitness, usually based on dominance (e.g., number of slaves or masters)
2. Method to maintain diversity in the set of points
3. Method to remember all good points seen during the search, usually using elitism or an archive

## Fitness Assignment in EC Approach

- Could use aggregation-based approach and change weights during evolution
- Different parts of population can use different criteria
- Dominance: ranking, fitness related to whole population

## Diversity Maintenance in EC Approach

Usually done by niching techniques such as:

- Fitness sharing
- Adding a number to fitness based on inverse distance to nearest neighbour (when fitness is to be minimized)
- (Adaptively) dividing search space into boxes and counting occupancy

All rely on some distance metric in the genotype / phenotype space

## Remembering Good Points in EC Approach

- Could just use elitist algorithm 
	- example: $(\mu+\lambda)$ replacement
- Common to maintain an archive of non-dominated points
	- some algorithms use this as a second population that can be used in recombination (Hall of Fame)
	- others divide archive into regions too
