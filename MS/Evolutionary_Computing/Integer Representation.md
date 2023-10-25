- Nowadays it is generally accepted that it **is better to encode numerical variables directly** (integers, floating point variables) **instead of encoding them as binaries**

- Some problems naturally have integer values, e.g. image processing parameters, were you have the natural ordering and notion of distance for numbers

- Others take categorical values from a fixed set e.g. {blue, green, yellow, pink}, where you do not have a logical order or distance measure – they are symbols, not numbers

- N-point / uniform crossover operators work as previously
- Bit-flip mutation can be generalized to random resetting: with probability $p_m$  a new value is chosen at random

- New options are possible, e.g., we can extend bit-flipping mutation to make a “creep” i.e. more likely to move to similar value (if similar is meaningful by adding a small (positive or negative) value to each allele with probability $p$.