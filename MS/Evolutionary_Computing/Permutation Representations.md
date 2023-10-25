Permutation representations are a special type of ordering or sequencing problems where the task is to arrange some objects in a certain order. 

## Definition of Permutation
A permutation is an arrangement of all the members of a set into some sequence or order. If the set has $n$ number of elements, then there are $n!$ (factorial of $n$) different ways to arrange these elements.
## Examples
1. **Production Scheduling**: The important aspect is the order in which elements are scheduled. For example, if we have 3 tasks A, B, and C, they can be scheduled in different orders like ABC, ACB, BAC, BCA, CAB, CBA. Each order is a permutation.

2. **Travelling Salesman Problem (TSP)**: The important aspect is the adjacency of elements, i.e., which elements occur next to each other. For example, if a salesman has to visit 3 cities A, B, and C, he can visit them in different orders like ABC, ACB, BAC, BCA, CAB, CBA. Each order is a permutation and represents a possible route for the salesman.

3. **Simple Example**: Consider a set of three elements {1, 2, 3}. The different permutations of this set are {1, 2, 3}, {1, 3, 2}, {2, 1, 3}, {2, 3, 1}, {3, 1, 2}, and {3, 2, 1}.

These problems are generally expressed as a permutation. If there are $n$ variables, then the representation is as a list of $n$ integers, each of which occurs exactly once.

## Mutation in Permutation Representations
In permutation representations, normal mutation operators can lead to inadmissible solutions.

Consider a gene $i$ with value $j$. If we apply a bit-wise mutation and change it to some other value $k$, it would mean that $k$ occurs twice and $j$ no longer occurs. This leads to an inadmissible solution. Hence, at least two values must be changed.

The mutation parameter now reflects the probability that some operator is applied once to the whole string, rather than individually in each position.

For example, consider a string of 5 genes represented as $\{1, 2, 3, 4, 5\}$. If we apply a mutation operator on the 2nd and 3rd genes, swapping their positions, we get $\{1, 3, 2, 4, 5\}$. This is a valid mutation as it doesn't lead to any repeated or missing values.

**Mathematical Representation**:
- Let a gene be represented as $i$ with a value $j$.
- After bit-wise mutation, the value changes to $k$.
- This implies that $k$ occurs twice and $j$ no longer occurs, leading to an inadmissible solution.
- Therefore, at least two values must be changed.
**Example:**
- Consider a string of 5 genes represented as $\{1, 2, 3, 4, 5\}$. We want to mutate the 2nd gene from $2$ to $3$.
- After mutation, we get $\{1, 3, 3, 4, 5\}$, which is inadmissible as $3$ occurs twice and $2$ is missing.
- To correct this, we change the original $3$ (at the 3rd position) to $2$. 
- So our valid mutated string is: $\{1, 3, 2, 4, 5\}$.

### Swap mutation
![[Swap_mut_img.png]]
- Pick two alleles at random and swap their positions
### Insert Mutation
![[Insert_mut_img.png]]
- Pick two allele values at random
- Move the second to follow the first,  shifting the rest along to accommodate
- Note that this preserves most of the order and the adjacency information
### Scramble mutation
![[Scramble_mut_img.png]]
- Pick a subset of genes at random
- Randomly rearrange the alleles in those positions
### Inversion mutation
![[Inversion_mut_img.png]]
- Pick two alleles at random and then invert the substring between them.
- Preserves most adjacency information (only breaks two links) but disruptive of order information


## Crossover
- “Normal” crossover operators will often lead to inadmissible solutions
- Many specialized operators have been devised which focus on  combining order or adjacency information from the two parents.
### Order 1 crossover
[Video explanation](https://www.youtube.com/watch?v=HATPHZ6P7c4)
- Idea is to preserve relative order that elements occur

**Informal procedure:**
1. Choose an arbitrary part from the first parent
2. Copy this part to the first child
3. Copy the numbers that **are not in the first part**, to the first child:
	- starting right from cut point of the copied part, 
	- using the order of the second parent 
	- and wrapping around at the end
4. Analogous for the second child, with parent roles reversed
**Example:**
 - Copy randomly selected set from first parent
![[Order1_xover_1_img.png]]
- Copy rest from second parent in order 1,9,3,8,2
![[Order1_xover_2_img.png]]

### Partially Mapped Crossover (PMX)
- This crossover method builds an offspring by choosing a sub-sequence of elements from one parent and preserving the order and position of as many elements as possible from the other parent
- A sub-sequence  of elements is selected by choosing two random cut points, which serve as boundaries for the swapping operations
#### Procedure
[Video explanation](https://www.youtube.com/watch?v=ZtaHg1C25Kk)
![[PMX_xover_img.png]]
1. Choose random segment and copy it from $P1$
2. Starting from the first crossover point look for elements in that segment of $P2$ that have not been copied
3. For each of these $i$ look in the offspring to see what element $j$ has been copied in its place from $P1$
4. Place $i$ into the position occupied by $j$ in $P2$, since we know that we will not be putting $j$ there (as is already in offspring)
5. If the place occupied by $j$ in $P2$ has already been filled in the offspring by $k$, put $i$ in the position occupied by $k$ in $P2$
6. Having dealt with the elements from the crossover segment, the rest of the offspring can be filled from $P2$.
#### Second Child
The same procedure is followed with $P1$ & $P2$ inverted.


### Cycle crossover
[Video explanation](https://youtu.be/DJ-yBmEEkgA?si=J92fMn2Fd-k7UDqP)
Each allele comes from one parent together with its *position*.

**Informal procedure:**
1. Make a cycle of alleles from P1 in the following way. 
	- Start with the first allele of P1. 
	- Look at the allele at the same position in P2.
	- Go to the position with the same allele in P1. 
	- Add this allele to the cycle.
	- Repeat step b through d until you arrive at the first allele of P1.
2. Put the alleles of the cycle in the first child on the positions they have in the first parent.

Step 1: identify cycles
![[cycle_xover_1_img.png]]
Step 2: copy alternate cycles into offspring
![[cycle_xover_2_img.png]]


### Edge Recombination
Works by constructing a table listing which edges are present in the two parents, if an edge is common to both, mark with a +

e.g. [1 2 3 4 5 6 7 8 9] and [9 3 7 8 2 6 5 1 4]
Edge Table:

| Element | Edges   | Element | Edges    |
| ------- | ------- | ------- | -------- |
| 1       | 2,9,5,4 | 6       | 5,7,2,5+ |
| 2       | 1,3,8,6 | 7       | 6,8,3,8+ |
| 3       | 2,4,9,7 | 8       | 7,9,7+,2 |
| 4       | 3,5,1,8 | 9       | 8,1,4,3  |
| 5       | 4,6,6,1 |         |          |

**Informal procedure:** once edge table is constructed
1. Pick an initial element, entry, at random and put it in the offspring
2. Set the variable current element = entry
3. Remove all references to current element from the table
4. Examine list for current element:
	- If there is a common edge, pick that to be next element
	- Otherwise pick the entry in the list which itself has the shortest list
	- Ties are split at random
1. In the case of reaching an empty list:
	- a new element is chosen at random

| Choices | Element Selected | Reason                                  | Partial Result              |
| ------- | ---------------- | --------------------------------------- | --------------------------- |
| All     | 1                | Random                                  | [1]                         |
| 2,9,5,4 | 5                | Shortest list                           | [1, 5]                      |
| 4,6     | 6                | Common edge                             | [1, 5, 6]                   |
| 7,2     | 2                | Random, 7,2 same len and 5 already used | [1, 5, 6, 2]                |
| 3,8     | 8                | Shortest list                           | [1, 5, 6, 2, 8]             |
| 7+,9    | 7                | Common                                  | [1, 5, 6, 2, 8, 7]          |
| 3       | 3                | Only item                               | [1, 5, 6, 2, 8, 7, 3]       |
| 4,9     | 9                | Random                                  | [1, 5, 6, 2, 8, 7, 3, 9]    |
| 4       | 4                | Last element                            | [1, 5, 6, 2, 8, 7, 3, 9, 4] |
