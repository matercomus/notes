# Parameter Tuning and Control in Evolutionary Algorithms

## Parameter Tuning
Parameter tuning involves testing and comparing different values before the "real" run. However, it has several problems:
- User mistakes in settings can be sources of errors or sub-optimal performance.
- It costs much time.
- Parameters interact: exhaustive search is not practicable.
- Good values may become bad during the run.

## Parameter Control
Parameter control involves setting values on-line, during the actual run. This can be done in several ways:
- Predetermined time-varying schedule $p = p(t)$.
- Using (heuristic) feedback from the search process.
- Encoding parameters in chromosomes and relying on natural selection.

However, parameter control also has its own problems:
- Finding optimal $p$ is hard, finding optimal $p(t)$ is harder.
- Still user-defined feedback mechanism, how to "optimize"?
- When would natural selection work for algorithm parameters?
- Doubling the task for the EA could slow down the runs.

## Notes on Parameter Control
Parameter control offers the possibility to use appropriate values in various stages of the search. Adaptive and self-adaptive control can "liberate" users from tuning, reducing the need for EA expertise for a new application. The assumption is that the control heuristic is less parameter-sensitive than the EA. However, the state-of-the-art is a mess: literature is a potpourri, no generic knowledge, no principled approaches to developing control heuristics (deterministic or adaptive), no solid testing methodology. So, what about automated tuning?

## Historical Account
Lately, there has been:
- More and more work on parameter control.
- Traditional parameters: mutation and crossover.
- Non-traditional parameters: selection and population size.
- All parameters leading to "parameter-less" EAs (interesting name choice!).

However, there has not been much work on parameter tuning, i.e.,
- Nobody reports on tuning efforts behind their EA published.
- Only a handful of papers on tuning methods/algorithms.

## Advantages of Tuning
- Easier to implement.
- Most immediate need of users.
- Control strategies have parameters too and need tuning themselves.
- Knowledge about tuning (utility landscapes) can help the design of good control strategies.
- There are indications that good tuning works better than control.
