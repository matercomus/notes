# Adaptive Memetic Algorithm

Adaptive Memetic Algorithms (MAs) are a type of Evolutionary Algorithm (EA) that incorporate local search or heuristic improvement. The choice of a good move/search operator is crucial in these algorithms. This can involve careful consideration, the use of domain-specific information, and the use of multiple local search operators in tandem. Some implementations even add a gene indicating which local search operator to use, which is inherited from parents and subject to mutation.

## Important Points

- **Hybrid Approach**: MAs are essentially EAs hybridized with other heuristics. They combine the "blind" evolution of EAs with problem-specific "intelligence".

- **Use of Intelligence**: This intelligence can come from known operators from other algorithms for the given problem (e.g., 2-opt for TSP), or from domain-specific or application-specific knowledge.

- **State of the Art**: MAs are considered the "state of the art" on many problems. They have been shown to be orders of magnitude faster and more accurate than EAs on some problems.

- **Real World Applications**: In real world applications, it is common to hybridise EAs. If you can hybridise, do it!
