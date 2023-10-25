## Heuristics for Initializing Population

### Process
For each individual in the initial population, an n-tournament is held amongst randomly created candidate solutions. This is not the same as taking the best popsize of n x popsize random points.

### Multi-Start Local Search
Pick popsize points at random, do some hill-climbing from these, and seed the initial population with the resulting points.

### Constructive Heuristics
Constructive Heuristics often exist and can be utilized in this process.

## Initialisation Issues

### Archive Approach
Initialize the population with solutions already known or found by another technique. However, be aware that performance may appear to drop at first if local optima on different landscapes do not coincide.

### Inoculating Population
Surry & Radcliffe (1994) studied ways of "inoculating" the population with solutions gained from previous runs or other algorithms/heuristics. They found that mean performance increased as the population was biased towards known solutions, but the best performance came from more random solutions.
