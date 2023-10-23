# Information Use in Local Search

Most Memetic Algorithms use an operator acting on a single point, and only use that information. However, this is an arbitrary restriction. Jones (1995), Merz & Friesleben (1996) suggest the use of a crossover hillclimber which uses information from two points in the search space. Krasnogor & Smith (2000) use information from the whole of the current population to govern acceptance of inferior moves. Tabu search with a common list could also be used.

# Diversity

Local search pushes strongly towards better points and is subject to quickly losing diversity. Some successful algorithms explicitly use mechanisms to preserve diversity. For example, Merz’s DPX crossover explicitly generates individuals at the same distance to each parent as they are apart. Krasnogor’s Adaptive Boltzmann Operator uses a Simulated-Annealing like acceptance criterion where “temperature” is inversely proportional to population diversity.

# Simulated Annealing

Simulated Annealing is a local search method or neighborhood search method, that is, generate and test. Some unary search/move/mutation operator steps from point/individual i  to its neighbor/child  j. Boltzmann selection with a parameter c > 0 called temperature, c is decreased over time (“cooling” schedule).

The probability of accepting j is given by:

$$P_c(accept(j))= \begin{cases} 
1 & \text{if } f(j) \leq f(i) \\
e^{\frac{f(i)-f(j)}{c}} & \text{if } f(i) < f(j) \\
\end{cases}$$

The impact of the constant c is as follows:

- If c is large, the exponent of e is small and < 0, so the term e^x is close to 1, making it very likely to accept worse neighbours.
- If c is small, the exponent of e is large and < 0, so the term e^x is close to 0, making it less likely to accept worse neighbours.
- Thus, a “cooling” schedule leads to more and more harsh selection.

# Boltzmann Selection Operator in an EA

The Boltzmann selection operator in an EA can be defined as:

$$P(acceptingneighbour)= \begin{cases} 
1 & \text{if } \Delta f>0 \\
e^{\frac{k\Delta f}{f_{max}-f_{avg}}} & \text{if } \Delta f<0 \\
\end{cases}$$

The induced dynamics are as follows:

- Early stage: The population is diverse so $f_{max} - f_{avg}$ is large. The exponent of e is small and < 0, so the term e^x is close to 1. This leads to exploration.
- Late stage: The population has converged so $f_{max} - f_{avg}$ is small. The exponent of e is large and < 0, so the term e^x is close to 0. This leads to exploitation.
