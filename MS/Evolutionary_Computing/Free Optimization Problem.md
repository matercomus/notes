# Free Optimization Problem (FOP)

An FOP is defined as $<S, f, •>$ where:
- $S$ is a free search space.
- $f$ is a real-valued objective function on $S$.

The solution of an FOP is $s \in S$ such that $f(s)$ is optimal in $S$. FOPs are considered 'easy' in the sense that it's 'only' optimizing with no constraints, and Evolutionary Algorithms (EAs) have a basic instinct for optimization.

## Example: Ackley Function
![[Ackely_func_img.png]]
The Ackley function is a well-known example of an FOP. The formula for the Ackley function is:

$$
f(x) = -20 \cdot exp\left(-0.2 \cdot \sqrt{\frac{1}{n} \cdot \sum_{i=1}^{n} x_i^2}\right) - exp\left(\frac{1}{n} \cdot \sum_{i=1}^{n} \cos(2\pi x_i)\right) + 20 + e
$$

where:
- $x = (x_1, ..., x_n)$ is a vector in the search space,
- $exp$ is the exponential function,
- $cos$ is the cosine function,
- $\pi$ is the mathematical constant Pi,
- $e$ is the mathematical constant Euler's number.
