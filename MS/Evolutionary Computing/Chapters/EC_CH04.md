## Representation, mutation, recombination

### Main Topics
- Role of [[representation]] and variation 
	- [[Representation#Two sides of representation|Two sides of representation]]
	- [[Representation#Representation (dis)continuity|Representation (dis)continuity]]
	- [[Representation#Strong causality principle|Strong causality principle]]
	- [[Representation#Good representations|Good representations ]]
- [[Binary Representation]]
- [[Integer Representation]]
- [[Real-Valued or Floating-Point Representation]]
- [[Mapping real values on bit strings]]
- [[Real-Valued Representation]]
- [[Permutation Representations]]
- [[Tree Representation]]
### Important points:
- Representation is essential when designing an EA
- A few data structures are enough to represent many (all?) problems, e.g., binary, integer, real-valued vectors, trees
- For any given problem there can be more suitable representations. Some are better than others – remember the strong causality principle !  
- Reproduction operators must fit the representation
- Reproduction operators are stochastic
- Reproduction operators can be distinguished by arity
	- Unary: mutation
	- Binary: recombination, crossover
	- N-ary: multi-parent recombination
- Self-adaptive mutation is a powerful mechanism. But remember to change the sigma **first**!