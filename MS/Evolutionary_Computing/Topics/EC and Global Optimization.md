Global optimization: search for finding best solution x* 
out of some fixed set S

- Deterministic approaches
	- e.g. box decomposition (branch and bound etc)
	- Guarantee to find $x^*$
	- May have bounds on runtime, usually super-polynomial 
 
- Heuristic approaches (generate and test)
	- rules for deciding which $x\in S$  to generate next
	- no guarantees that best solutions found are globally optimal
	- no bounds on runtime
### Neighborhood Search

Many heuristics impose a neighborhood structure on S

- Such heuristics may guarantee that best point found is locally optimal  e.g. Hill-Climbers: 
	- But problems often exhibit many local optima  
	- Often very quick to identify good solutions
 
- EAs are distinguished by (the combination of) the following:
	- Use of population
	- Use of multiple, stochastic search operators 
	- [[Variation Operators]] with arity >1, thus combining information of more candidate solutions
	- Stochastic selection

Question: what is a neighborhood in an EA? #TODO 