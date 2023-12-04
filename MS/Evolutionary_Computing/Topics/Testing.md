# Testing Parameter Vectors in Evolutionary Algorithms

## Generate-and-test
![[Tuning_gen_and_test_1_img.png]]
When testing parameter vectors in evolutionary algorithms, the following steps are typically followed:
### Procedure
1. **Run EA with these parameter values on the given problem(s)**: This involves executing the algorithm with a specific set of parameter values.
2. **Record EA performance in each run**: The performance of the EA is recorded for each run. This can be done by tracking:
	- **Solution** quality: The best fitness at termination.
	- **Speed**: The time used to find the required solution quality.
1. **Repetitions for reliable evaluation**: Since EAs are stochastic, multiple runs are needed for a reliable evaluation. This provides statistics on average performance by solution quality, speed (MBF, AES), success rate (percentage of runs ending with success), and robustness (variance in those averages over different problems).
### Under the hood
![[Tuning_gen_and_test_2_img.png]]

## Types of Parameters

### Numeric Parameters
![[Num_param_img.png]]
These include parameters like population size, crossover rate, tournament size, etc. Their domain is a subset of R, Z, N (finite or infinite). They have a sensible distance metric and are searchable.
### Symbolic Parameters
![[Sym_param_img.png]]
These include parameters like crossover operator, elitism, selection method, etc. Their domain is finite (e.g., {1-point, uniform, averaging}, {Y, N}). They do not have a sensible distance metric and must be sampled.

### Notes on Parameters
A given value of a symbolic parameter can introduce a numeric parameter. For example, if selection is set to tournament, it introduces the tournament size parameter. If population type is set to overlapping, it introduces the generation gap parameter. Hence, parameters can have a hierarchical, nested structure.

The number of EA parameters is not defined in general. The design space or tuning search space cannot simply be denoted by 
$$S = Q_1 x … Q_m x R_1 x … x R_n$$ where $Q_i / R_j$ are the domains of the symbolic/numeric parameters.
