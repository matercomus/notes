# Two Approaches to Multi-objective Optimization

## Preference-based Approach

Also known as the aggregation-based approach, this method:

- Transforms the problem into a single objective one, and
- Solves it with a single objective optimization method
- Uses higher level information that imply preferences on the importance of objectives
- Sets weights for objectives & makes a weighted sum to be the single objective
- The weights represent the relative importance of the objectives
- This results in a particular trade-off solution

### Example: Weighted-sum Approach

The modified problem is defined as:

$$F(x)= \sum_{m=1}^{M}{w_m f_m(x)}$$ 

where $w_m \in [0,1]$ and $\sum_{m=1}^{M}{w_m}=1$

![[Weighted_sum_approach_img.png]]
Weights define an angle, hence hyper-planes in the objective space, these define the Pareto front.

## Real Multi-objective Approach

This approach:
- Uses a multi-objective optimization method 
- Results in multiple trade-off solutions
- Chooses a particular trade-off solution using higher-level information / preferences on importance of objectives
- These preferences may not be quantified in advance, and may not be quantifiable at all