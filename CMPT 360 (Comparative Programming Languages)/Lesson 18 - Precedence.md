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
	1. Exponention (if available) `**` or `∧`
	2. `* / MOD DIV REM AND`
	3. Term Operators (monadic or dynadic) `+ - OR`
	4. Relational operators `< > # <= >= = <>` modified by function calls and parenthesis.
		- C++ has many more, assigning precedence numbers in part.
##### Associativity
- We expect left-right (from mathematics) whenever two operators have the same precedence.
- However, a grammar for a typical LL parser has the optimal parts on the right which forces right-left associativity so that `2 - 3 - 4 = 2 - -1 = 3`
- Fortran exponentiation is like that (right-left)
	- e.g. `a**b**c` means `a^(b^c)`
- C prefix ++ -- and monadic +-
- Ada exponentiation is not associative so `a**b**c` is illegal.
- APL has no precedence and goes strictly left-right (arithmetic style)
- Ada boolean operations have the same precedence so must be parenthesized.
- In a function or procedure call f(x,y,z,a), the order of parameter evaluation may be:
	- left-right (java)
	- right-left
	- undefined (Modula-2, C++)
- So a program whose meaning depends on this is incorrect.
##### Type Changing
- Type changing as part of an expression may be...
###### Widening
- Widening is a change to a type that can include at least approximations of all values of the original type.
	- e.g. int --> float (even if of less precision)
###### Narrowing
- A change to a type that cannot include even approximations of some values of the original type.
	- e.g. `LONGREAL --> REAL`, `double --> float`, `int --> byte` or `OCTET`
###### Safe (Conversions)
- Data is reformatted to the new type.
###### Unsafe (Coercions)
- Bit patterns are forcibly reinterpreted but they are not changed.
	- **Note**: Many texts and some languages get this wrong, using CAST for both, when it should only be applied to the second.
###### Implicit
- The compiler intuits a conversion automatically (only in weakly types languages). This is not a coercion.
	- e.g. `floatVariable = floatVariable + 4`
	- If such mixed expressions are allowed, the int value is automatically converted.
###### Explicit
- The conversion is/has to be initiated by specific syntax.
- In strongly types languages it must be done this way.
	- `realVar := FLOAT(intVar) + 2.5`
	- `realVar := VAL(real, intVar) + 2.5E + 0.5`
	- `intVar := (int)realAngle`
- C calls the last one a CAST but it is a conversion.
	- `myBitSet := SYSTEM.CAST(BITSET, theCardinal)` (This one is a coercion)
- Note that in Java, `realVar = realVar + 4` does not strictly speaking involve a conversion because Java doesn't have whole number arithmetic so 4 is stored as a floating point value.
##### Assignment
- `<target><assignOperator><expression>`
- `<assignOperator>` may be `:=` or just `=` (overloaded)
##### Variations and Issues:
1. Multiple Assignments