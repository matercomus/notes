# Chapter 8: Parameter Control in Evolutionary Computing
![[Parameter_taxonomy_img.png]]
## Motivation
An Evolutionary Algorithm (EA) has many strategy parameters, such as:
- Mutation operator and mutation rate
- Crossover operator and crossover rate
- Selection mechanism and selective pressure (e.g., tournament size)
- Population size

Good parameter values facilitate good performance. However, this leads to two key questions:

1. **How to find good parameter values?**
   Finding the right values for these parameters can significantly impact the performance of the EA. This process is often referred to as parameter tuning.
2. **How to vary parameter values?**
   EA parameters are typically rigid, with values remaining constant during a run. However, an EA is a dynamic, adaptive process. Thus, the optimal parameter values may vary during a run. This process is often referred to as parameter control.

- [[Examples of parameter control]]
## Primary Features
- What component of the EA is changed.
- How the change is made.

## Secondary Features
- Evidence/data backing up changes.
- Level/scope of change.

## What Component is Controlled
Practically any EA component can be parameterized and thus controlled on-the-fly:
- Representation.
- Evaluation function.
- Variation operators.
- Selection operator (parent or mating selection).
- Replacement operator (survival or environmental selection).
- Population (size, topology).

## How are Parameters Controlled
Three major types of parameter control:
- **Deterministic**: Some rule modifies strategy parameter without feedback from the search (based on some counter).
- **Adaptive**: Feedback rule based on some measure monitoring search progress.
- **Self-adaptive**: Parameter values evolve along with solutions; encoded onto chromosomes they undergo variation and selection.

## Evidence: Informing the Change
The parameter changes may be based on:
- Time or number of evaluations (deterministic control).
- Population statistics (adaptive control).
	- Progress made.
	- Population diversity.
	- Gene distribution, etc.
- Relative fitness of individuals created with given values (adaptive or self-adaptive control).

## Refined Taxonomy
Combinations of types and evidences:

|          | Deterministic | Adaptive | Self-adaptive |
| -------- | ------------- | -------- | ------------- |
| Absolute | +             | +        | -             | 
| Relative | -             | +        | +             |

## Scope/Level
The parameter may take effect on different levels:
- Environment (fitness function).
- Population.
- Individual.
- Sub-individual.

Note: Given component (parameter) determines possibilities. Thus, scope/level is a derived or secondary feature in the classification scheme.

## Lessons Learned

|          | $\sigma=1-0.9\frac{t}{T}$ | $\sigma'=\sigma/c$, if $r>\frac{1}{5}$ | $(x_1, ..., x_n, \sigma_1, ..., \sigma_n)$ | $W(t)=(C*t)^a$ | $W'=\beta*W$ if $b_1 \in f$ | $(x_1, ..., x_n, W)$            |
| -------- | ------------------------- | -------------------------------------- | ------------------------------------------ | -------------- | --------------------------- | ------------------------------- |
| What     | Step size                 | Step size                              | Step size                                  | Step size      | Penalty weight              | Penalty weight                  |
| How      | Deterministic             | Adaptive                               | Self-adaptive                              | Self-adaptive  | Deterministic               | Adaptive                        |
| Evidence | Time                      | Successful mutations rate              | (Fitness)                                  | (Fitness)      | Time                        | Constraint satisfaction history |
| Scope    | Population                | Population                             | Individual                                 | Gene           | Population                  | Population                      |

## Evaluation/Summary
Parameter control offers the possibility to use appropriate values in various stages of the search. Adaptive and self-adaptive parameter control offer users "liberation" from parameter tuning and delegate parameter setting task to the evolutionary process. The latter implies a double task for an EA: problem solving + self-calibrating (overhead).
