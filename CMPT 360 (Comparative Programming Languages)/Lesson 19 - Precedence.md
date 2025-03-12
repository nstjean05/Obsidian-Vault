#incomplete
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
	- If `=` is used, what does `a=b=c` mean?



**19.  _Precedence issues, Conversions, mixed mode, other issues_**

**[5+3]** a. Provide a complete precedence table for C++ and for Python.
C++ Operator Precedence Table (cppreference.com)

| Precedence | Operator(s)                                                                             | Description                        | Associativity |
| ---------- | --------------------------------------------------------------------------------------- | ---------------------------------- | ------------- |
| 1          | ::                                                                                      | Scope resolution                   | Left to Right |
| 2          | ++, --, (), [], . , ->, typeid, const_cast, dynamic_cast, reinterpret_cast, static_cast | Postfix operators and type casting | Left to Right |
| 3          | ++, --, +, -, !, ~, *, &, sizeof, new, delete                                           | Unary operators                    | Right to Left |
| 4          | .*, ->*                                                                                 | Pointer-to-member                  | Left to Right |
| 5          | *, /, %                                                                                 | Multiplication, Division, Modulus  | Left to Right |
| 6          | +, -                                                                                    | Addition, Subtraction              | Left to Right |
| 7          | <<, >>                                                                                  | Bitwise Shift Operators            | Left to Right |
| 8          | <, <=, >, >=                                                                            | Relational Operators               | Left to Right |
| 9          | ==, !=                                                                                  | Equality Operators                 | Left to Right |
| 10         | &                                                                                       | Bitwise AND                        | Left to Right |
| 11         | ^                                                                                       | Bitwise XOR                        | Left to Right |
| 12         | `                                                                                       | `                                  | Bitwise OR    |
| 13         | &&                                                                                      | Logical AND                        | Left to Right |
| 14         | `                                                                                       |                                    | `             |
| 15         | ?:                                                                                      | Ternary Operator                   | Right to Left |
| 16         | =, +=, -=, *=, /=, %=                                                                   | Assignment Operators               | Right to Left |
| 17         | ,                                                                                       | Comma Operator                     | Left to Right |

Python Operator Precedence Table (GeeksforGeeks.com)

|Precedence|Operator(s)|Description|Associativity|
|---|---|---|---|
|1|()|Parentheses (grouping)|Left-to-right|
|2|x[index], x[index:index], x(arguments...), x.attribute|Subscription, slicing, function call, attribute reference|Left-to-right|
|3|await x|Await expression|Right-to-left|
|4|**|Exponentiation|Right-to-left|
|5|+x, -x, ~x|Unary plus, unary minus, bitwise NOT|Right-to-left|
|6|*, @, /, //, %|Multiplication, matrix multiplication, division, floor division, modulo|Left-to-right|
|7|+, -|Addition and subtraction|Left-to-right|
|8|<<, >>|Bitwise left shift and right shift|Left-to-right|
|9|&|Bitwise AND|Left-to-right|
|10|^|Bitwise XOR|Left-to-right|
|11|\||Bitwise OR|Left-to-right|
|12|in, not in, is, is not, <, <=, >, >=, !=, ==|Comparisons, including membership and identity tests|Left-to-right|
|13|not x|Logical NOT|Right-to-left|
|14|and|Logical AND|Left-to-right|
|15|or|Logical OR|Left-to-right|
|16|if – else|Conditional expression|Right-to-left|
|17|lambda|Lambda expression|Right-to-left|
|18|:=|Assignment expression (walrus operator, introduced in Python 3.8)|Right-to-left|
**[4]** b. What are your own arguments for and against allowing mixed-mode arithmetic expressions with implicit conversion where applicable?
- The is the primary advantage of allowing mixed-mode arithmetic expressions with implicit conversions is the simplification for users. Programmers, especially those who need to write rapidly or who are new to programming, may find it more efficient to not need to worry about adding a float to an integer. However, given a wider view, I think that allowing for this is not a great idea. Although there are errors in the moment, it will increase more subtle errors/inaccuracies over time, and allows for more catastrophic mistakes to be made. Additionally, new programmers may then have difficulty translating their knowledge into other languages. Debugging becomes more complex, as there are a wider range of points of failure.

**[4]** c. Do you think that eliminating all overloading of operators in your favourite language would be desirable? feasible?
- In Python, I think that this would not be a very desirable change. Not only do I think it is generally poor practice to completely remove a functionality from a language, but it would also serve to make the language worse. Overloading of operators greatly enhances code readability and increases functionality in a program. For instance, it is not feasible to remove overloading of operators without severely impairing object-oriented programming --  a critical aspect of Python. Furthermore, Python uses a overloading internally (ex. adding strings), and so it would incapacitate core aspects of the language.
https://www.geeksforgeeks.org/operator-overloading-in-python/

**[4]** d. Would it be a good idea to eliminate all precedence rules and use parentheses instead? Why or why not?
- I am actually something of a proponent of using parenthesis in many applications. Especially when entering a complex function into some sort of system, explicitly declaring the precedence using parenthesis drastically saves time by increasing reliability. However, I do not think that this is a good idea in much of programming. While parenthesis may suit simple equations, tracking open and closed sides can become progressively more difficult with more complexity. There is also a great detriment to readability, as it can be hard to tell where in a functions the values and operators actually lie. Additionally, there are many scenarios where it would be much more roundabout to use parenthesis, rather than use the built-in precedence of the language.

**[4]** e. Should the assigning operator += from C be used in other languages? Why or why not?
- I think it is good for the addition assignment operator (*+=*) to be used in multiple languages. It allows for a value be added with another, in short form (ex. *a = a + b* becomes *a += b*). This compound operator is useful, as it can enhance writability, with very little detriment to readability. In many cases it can actually enhance readability, as it serves to declutter equations. On top of the surface-level benefits, 

**[4]** f. Describe a situation, and write some code to illustrate that the addOperator + may not always be commutative.

**[4]** g. Write a program in a language of your choice that dows a large number of floating point operations and the same number of integer operations (hand in code) and compare the time taken. Explain.