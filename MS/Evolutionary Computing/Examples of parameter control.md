# Parameter Control in Evolutionary Computing Algorithms: Examples

## Task
- Minimize the function: $$f(x_1,…,x_n)$$
- Bounds: $L_i \leq x_i \leq U_i$ for i = 1,…,n
- Inequality constraints: $g_i (x) \neq 0$ for i = 1,…,q
- Equality constraints: $h_i (x) = 0$ for i = q+1,…,m

## Algorithm
- EA with real-valued representation $(x_1,…,x_n)$
- Arithmetic averaging crossover
- Gaussian mutation: $x'_i = x_i + N(0, σ)$
- Standard deviation σ is called mutation step size 

### Varying Mutation Step Size

#### Option 1
Replace the constant σ by a function σ(t) where 0 < t <= T is the current generation number. Features:
- Changes in σ are independent from the search progress.
- Strong user control of σ by the above formula.
- σ is fully predictable.
- A given σ acts on all individuals of the population.

The formula is: $σ(t)= 1 - 0.9 ×\frac{t}{T}$
#### Option 2
Replace the constant σ by a function σ(t) updated after every n steps by the 1/5 success rule, where ps is the % of successful mutations. Features:
- Changes in σ are based on feedback from the search progress.
- Some user control of σ by the above formula.
- σ is not predictable.
- A given σ acts on all individuals of the population.

The formula is: 
$$\sigma(t) = \begin{cases} 
\sigma \cdot c & \text{if } p_s(t) > n \\
\sigma / c & \text{if } p_s(t) < n \\
\sigma & \text{otherwise}
\end{cases}$$
#### Option 3
Assign a personal σ to **each individua**l and incorporate this σ into the chromosome: $(x_1, …, x_n, σ)$. Apply variation operators to xi‘s and σ. Features:
- Changes in σ are results of natural selection.
- (Almost) no user control of σ.
- σ is not predictable.
- A given σ acts on one individual.

The formulas are: 
$\sigma'=\sigma e^{N(0,\sigma)}$
$x'_i=x_i+N(0,\sigma)$

#### Option 4
Assign a personal σ to **each variable** in each individual and incorporate σ’s into the chromosomes: $(x_1, …, x_n, σ_1, …,  σ_n)$. Apply variation operators to xi‘s and σi‘s. Features:
- Changes in σi are results of natural selection.
- (Almost) no user control of σi.
- σi is not predictable.
- A given σi acts on one gene of one individual.

The formulas are: 
$\sigma'=\sigma e^{N(0,\sigma)}$
$x'_i=x_i+N(0,\sigma)$

### Varying Penalties
Constraints are handled by penalties:
- Inequality constraints: $g_i (x) \neq 0$ for i = 1,…,q
- Equality constraints: $h_i (x) = 0$$ or i = q+1,…,m

The evaluation function is defined as: 
$$eval(x) = f(x) + W \times penalty(x)$$
where 
$$penalty(x) = \sum_{j=1}^{m} \begin{cases} 
0 & \text{if constraint is satisfied} \\
1 & \text{if constraint is violated}
\end{cases}$$
#### Option 1
Replace the constant W by a function W(t) where 0 < t <= T is the current generation number. Features:
- Changes in W are independent from the search progress.
- Strong user control of W by the above formula.
- W is fully predictable.
- A given W acts on all individuals of the population.

The formula is: $W(t)= C \times \alpha^t$
#### Option 2
Replace the constant W by W(t) updated in each generation. Features:
- Changes in W are based on feedback from the search progress.
- Some user control of W by the above formula.
- W is not predictable.
- A given W acts on all individuals of the population.

The formula is: 
$$W(t+1) = \begin{cases} 
W(t) \times \beta & \text{if all champions in last k generations are feasible} \\
W(t) \times \gamma & \text{if all champions in last k generations are infeasible} \\
W(t) & \text{otherwise}
\end{cases}$$
where $\beta < 1, \gamma > 1, \beta \times \gamma \neq 1$

#### Option 3
Assign a personal W to each individual and incorporate this W into the chromosome: $(x_1, …, x_n, W)$. 
Apply variation operators to xi‘s and W. Note that this option is sensitive to "cheating" and makes no sense because we have 
$$eval ((x, W)) = f (x) + W \times penalty(x)$$ while for mutation step sizes we had $eval ((x, σ)) = f (x)$. 