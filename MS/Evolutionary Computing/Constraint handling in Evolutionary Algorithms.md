# Solving CSPs by EAs

Evolutionary Algorithms (EAs) need an objective function $f$ to optimize. Thus, a Constraint Satisfaction Problem (CSP) defined as $<S, •, \phi>$ must be transformed into either:

1. **FOP (Free Optimization Problem)**: The transformation is $<S, •, \phi> \rightarrow <S, f, •>$
	All constraints become objectives.
1. **COP (Constrained Optimization Problem)**: The transformation is $<S, •, \phi> \rightarrow <S, f, Ψ >$. Some constraints become objectives, but not all.

The transformation must be (semi-)equivalent, i.e., at least:
- If $f(s)$ is optimal in $S$, then $\Phi(s) = true$.
- If $\psi(s) = true$ and $f(s)$ is optimal in $S$, then $\Phi(s) = true$.

## Direct vs. Indirect Constraint Handling

- **[[Indirect Constraint Handling]]**: Transforming the constraint into an objective. This happens **before** running the EA (to create an $f$).
- **[[Direct Constraint Handling]]**: Taking care that the constraint is respected. This happens **during** running the EA.

A CSP to FOP transformation means all **constraints** are handled **indirectly**. 
A CSP to COP transformation means some **constraints** are handled **indirectly, and some are handled directly**.
