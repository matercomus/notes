In genetic algorithms, we often need to represent real numbers using bit strings. This is done through a process called **mapping**.

## The Mapping Process

Consider a real number $z \in [x, y] \subseteq \mathbb{R}$ that we want to represent using a bit string $\{a_1,…,a_L\} \in \{0,1\}^L$ where $L$ is the user-defined chromosome length. 

The mapping from $[x,y]$ to $\{0,1\}^L$ must be invertible, meaning that each phenotype (the set of observable characteristics or properties of an organism) must correspond to one and only one genotype (the genetic constitution of an organism).

We define a function $\Gamma: \{0,1\}^L \rightarrow [x,y]$ that describes this representation.

## Limitations and Precision

It's important to note that only $2^L$ values out of an infinite number can be represented. This is due to the binary nature of bit strings. 

The value of $L$ determines the maximum possible precision of the solution. A higher precision requires longer chromosomes, which can slow down the evolution process in genetic algorithms.

## Example

Let's consider an example where we want to map the real number range $[0, 10]$ to a bit string of length $L=4$. 

In this case, we have $2^4 = 16$ possible values that can be represented. If we want to represent the number 5, we could use the bit string `0101`.

Remember that increasing the length of the bit string will increase the precision but also slow down the evolution process.
