- **Objective function**: a way of assigning a value to a possible solution that reflects its quality on scale
	- Number of un-checked queens (maximize)
	- Length of a tour visiting given set of cities (minimize)
- **Constraint**: binary evaluation telling whether a given  requirement holds or not
	- Property of a chessboard configuration: are there queens that check each other? (we are good if “no”)
	- Property of a tour: is city X is visited after city Y? (we are good if “yes”)

When combining the two, note that constraint problems can be transformed into optimization problems.

|                  | Objective Function: Yes | Objective Function: No          |
| ---------------- | ----------------------- | ------------------------------- |
| Constraints: Yes | COP                     | CSP |
| Constraints: No  | FOP                     | NP                              |

- **COP**: Constrained Optimisation Problem
- **FOP**: Free Optimization Problem
- **CSP**: Constraint Satisfaction Problem
- **NP**: No Problem

Note: constraint problems can be transformed into optimization problems