# Parameter Tuning Examples

## Example Study: 'Best Parameter Values'
- **Setup**: The problem was the Sphere Function (unimodal, simple, often used to test algorithm speed). The EA was defined by Tournament Parent Selection, Random Uniform Survivor Selection, Uniform Crossover, BitFlip Mutation. The tuner was REVAC spending X units of tuning effort, tuning for speed. A = 1000, B = 30, C = 10000.
- **Results**: The best EA had the following parameter values: Population Size: 6, Tournament Size: 4, etc.
- **Conclusions**: For this problem we need a high (parent) selection pressure. This is probably because the problem is unimodal.

## Example Study: 'Good Parameter Values'
- **Setup**: Same as before.
- **Results**: The 25 best parameters vectors have their values within the following ranges: Mutation Rate: [0.01, 0.011], Crossover Rate:[0.2, 1.0], etc.
- **Conclusions**: For this problem the mutation rate is much more relevant than the crossover rate.

## Example Study: 'Interactions'
![[Example_study_ineractions_graph_img.png]]
- **Setup**: Same as before.
- **Results**: Plotting the population size and generation gap of the best parameter vectors shows a certain pattern.
- **Conclusions**: For this problem the best results are obtained when (almost) the complete population is replaced every generation.
