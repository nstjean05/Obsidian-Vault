- There are 3 general kinds of precedence for expression
#### 1. Arithmetic
- Scanning is strictly left to right, modified only by parenthesis
- e.g. `4 + 5 + 6 = 9 * 6 = 54` or `4 + (5 * 6) = 4 + 30 = 34`
#### 2. Algebraic
- Scanning follows algebraic rules:
	- Factor operators before term operators, modified by parenthesis.
	- Parenthesis include absolute values and function calls.
#### 3. Enhanced Algebraic for Programming Languages
##### Typical
1. Logical negation, e.g. `NOT`
2. nuL-operators
	1. Exponention (if available) `**` or ``