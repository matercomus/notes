# Tuning Effort

The total amount of computational work is determined by:
- **Number of vectors tested**: This is the number of different sets of parameter values that are tried.
- **Number of tests per vector**: This is the number of times each set of parameter values is tested.
- **Number of fitness evaluations per test**: This is the number of times the fitness function is evaluated for each test.

## Categories

Tuning methods can be positioned by their rationale:
- **To optimize the number of vectors tested (iterative search)**: This involves finding the best set of parameter values by trying different combinations.
- **To optimize the number of tests per vector (multi-stage search)**: This involves reducing the number of times each set of parameter values is tested.
- **To optimize both the number of vectors tested and the number of tests per vector (combination)**: This involves both finding the best set of parameter values and reducing the number of tests per vector.
- **To optimize the number of fitness evaluations per test (non-existent)**: This would involve reducing the number of fitness evaluations per test, but such methods do not currently exist.

### **Optimizing the Number of Vectors Tested**
- This approach is applicable only to **numeric parameters**.
- The goal is to find the optimal set of parameter values by testing different combinations.
- The number of tested vectors is not fixed, it is determined by a stop condition.
- Population-based search involves:
	- Initializing with a small number of vectors
	- Iterating: generating, testing, selecting parameter vectors.
- Some methods include Meta-EA, SPO, and REVAC.

### **Optimizing the Number of Tests Per Vector**
- This approach is applicable to **symbolic and numeric parameters**.
- The goal is to reduce the number of times each set of parameter values is tested.
- The number of tested vectors is fixed at initialization.
- The set of tested vectors can be created by:
	- Regular method (grid search)
	- Random method (random sampling)
	- Exhaustive method (enumeration).
- Complete testing involves a single stage while selective testing involves multiple stages.

### **Optimizing Both the Number of Vectors Tested and the Number of Tests Per Vector**
Existing work includes Meta-EA with racing, sharpening, and improved methods like REVAC with racing & sharpening = REVAC++.

## **Which Tuning Method?**
Differences between tuning algorithms include maximum utility reached, computational costs, number of their own parameters – overhead costs, and insights offered about EA parameters. Similarities between tuning algorithms include the ability to find good parameter vectors, lack of usage, and rarity of solid comparisons.