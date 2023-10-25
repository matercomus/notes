### Role: generate new candidate solutions

Usually divided into two types according to their arity (number of inputs):
- Arity = 1: **[[mutation]]** operators
- Arity > 1: **[[recombination]]** operator
	- Arity = 2: typically called **[[crossover]]**
	- Arity > 2: **multi-parent reproduction**, is possible, seldom used in EC.
  
- There has been much debate about relative importance of recombination and mutation
- Nowadays most EAs use both – pragmatic attitude is advisable

- *Variation operators **must match** the given **[[representation]]**!*
