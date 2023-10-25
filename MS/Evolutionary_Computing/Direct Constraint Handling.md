# Direct Constraint Handling

Direct constraint handling involves dealing with constraints during the execution of the Evolutionary Algorithm (EA). Here are some options:

1. **Eliminating infeasible candidates**: This is very inefficient and hardly practicable.
2. **Repairing infeasible candidates**: This is problem-specific and may or may not be possible/easy.
3. **Preserving feasibility by special mutation / crossover operators**: This requires a feasible initial population.
4. **Decoding, i.e., transforming the search space**: This allows for the usual representation and operators.

##### **Question**: Which of these did you see in the N-queens example?
In the N-queens problem, we typically see the use of the **repairing infeasible candidates** and **preserving feasibility by special mutation / crossover operators** strategies for direct constraint handling.

- **Repairing infeasible candidates**: When a candidate solution violates the constraints (i.e., two or more queens threaten each other), we can repair it by moving queens to safe positions.
- **Preserving feasibility by special mutation / crossover operators**: Specialized mutation and crossover operators can be designed to always generate feasible offspring. For example, a mutation operator could randomly select a queen and move it to a safe position, and a crossover operator could combine parts of two parent solutions in a way that doesn't violate the constraints.

Please note that these strategies are problem-specific and their effectiveness can vary depending on the problem and the specific implementation of the EA.


## Pros and Cons of Direct Constraint Handling

**Pros**:
- It works well (except eliminating).

**Cons**:
- It's problem-specific.
- There are no guidelines.
