### Role
- Identifies individuals 
	- to become parents
	- to survive
- Pushes population towards higher fitness
- Usually probabilistic / stochastic
	- high quality solutions more likely to be selected than low quality
	- but not guaranteed
	- even worst in current population usually has non-zero probability of being selected
- This *stochastic* nature can help escape from local optima

### Example: Roulette wheel selection
![[Roulette_wheel_selection_img.png]]
In principle, any election mechanism can be used for parent selection as well as for survivor selection.

### Summary
- Survivor selection a.k.a. replacement
- Most EAs use fixed population size so need a way of going from parents + offspring to next generation

- Often deterministic (while parent selection is usually stochastic)

- Fitness based : e.g., rank parents + offspring and take best 
- Age based: e.g., make as many offspring as parents and delete all parents 

- Sometimes a combination of stochastic and deterministic, for example:
	- **Elitism**: the best n individuals always survive (deterministic rule). This can be combined with as stochastic rule for the others.