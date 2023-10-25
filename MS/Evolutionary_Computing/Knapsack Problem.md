# Knapsack Problem

The Knapsack Problem is a combinatorial optimization problem. Given a knapsack with finite capacity $C$ and a set of $n$ items, where each item $i$ is associated with a weight $w_i$ and a profit $p_i$, the goal is to select a subset of items such that the total profit $z$ is maximized, while the total weight $b$ does not exceed the capacity of the knapsack, $C$. 

The problem can be formulated as follows:

Maximize:
$$z=\sum_{i=1}^{n}{x_ip_i}$$

Subject to:
$$b=\sum_{i=1}^{n}{x_i w_i}\leq c$$

and $x_i \in \{0,1\}$, for $i= 1, 2,..., n$

Here, $x_i = 1$ if item $i$ is chosen and $0$ otherwise.
## Knapsack Problem: Example

Consider an example of the Knapsack Problem with $n=7$ and $c=100$. The weights and profits of the items are given in the table below:

| $i$     | 1   | 2   | 3   | 4   | 5   | 6   | 7   |
| ----- | --- | --- | --- | --- | --- | --- | --- |
| $w_i$ | 40  | 50  | 30  | 10  | 10  | 40  | 30  |
| $p_i$ | 40  | 60  | 10  | 10  | 3   | 20  | 60  |

### Local Search Method: 1 Bit Flip

In this method, we choose the bit flip resulting in a feasible solution with the highest weight increase. We repeat this until each bit flip results in an infeasible solution. 

#### 1 Bit Flip example solution

| iteration | current string | best flipped bit | best neighbor | new $b$ | new $z$ | 
| --------- | -------------- | ---------------- | ------------- | ------- | ------- |
| 1         | 0000000        | 7                | 0000001       | 30      | 60      |
| 2         | 0000001        | 2                | 0100001       | 80      | 120     |
| 3         | 0100001        | 4                | 0101001       | 90      | 130     |
| 4         | 0101001        | 5                | 0101101       | 100     | 133     |
| 5         | 0101101        | -                | converge      | -       | -       |

If we start with the initial solution `0000000`, after applying the local search method, we get the solution `0101101` (b=100,z=133). The result increased by about 33% compared to the blind approach.
### Local search without problem specific knowledge: first fit

Starting from initial solution, examine the inclusion of an item in the order of i=1,2,..
Item is included if there is still room for the item.
#### First Fit example solution

| iteration | current string | best flipped bit | best neighbor | new $b$ | new $z$ |
| --------- | -------------- | ---------------- | ------------- | ------ | ------ |
| 1         | 00001000       | 1                | 10001000      | 40     | 40     |
| 2         | 10001000       | 2                | 11001000      | 90     | 100    |
| 3         | 11001000       | -                | converge      | -      | -      |

Starting with the initial solution `00001000`, after applying the first fit method, we get the solution `11001000` (b=90,z=100).

### Local Search with Problem Specific Knowledge: First Fit Descent

In this method, we calculate for each item the ratio $p_i/w_i$, sort the items in decreasing value, and add items in this order as long as there is room. 

#### First Fit Descent example solution

| iteration | current string | best flipped bit | best neighbor | new $b$ | new $z$ |
| --------- | -------------- | ---------------- | ------------- | ------- | ------ |
| 1         | 00001000       | 7                | 00001001      | 40      | 63     |
| 2         | 00001001       | 2                | 01001001      | 90      | 123    |
| 3         | 01001001       | -                | converge      | -       | -      |

Starting with the initial solution `00001000`, after applying the first fit descent method, we get the solution `01001001` (b=90,z=123). The result increased by about 23% compared to the first fit approach.