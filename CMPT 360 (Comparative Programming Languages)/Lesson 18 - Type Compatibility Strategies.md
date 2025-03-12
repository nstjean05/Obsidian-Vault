#incomplete
#### Type Compatibility Strategies
1. **By Name** (explicit)
	- Two items must be formally declared of the same type to be compatible.
2. **By Structure** (implicit)
	- Two items are compatible if they have the same structure.
```
type
	Array1 = array[0..5] of float
	Array2 = array[0..5] of float
	Array3 = Array2
var
	a1:Array1
	a2:Array2
	a3:Array3
	...
	a2 = a1;
	a3 = a2
```
- Note: Most languages have a mix of the two except that...
	- Literate languages lean toward the first
	- C-like languages lean toward the second
3. **Sub-Types**
	- A subtype is compatible with its parent type.
	- e.g. In ISO Modula-2
		- Z-type incorporates all whole number types, with CARDINAL and INTEGER subtypes and `TYPE digit = [0..9]` is compatible with z-type
	- e.g. In Ada
		- `TYPE DIGIT` is `INTEGER` range `0..9` is compatible with `INTEGER`
4. **Ada Derived Types**
	- `type MYREAL is now FLOAT`
		- Creates a derived type with all the same properties as FLOAT but is not compatible with FLOAT
5. **Anonymous Types**
	- Some languages permit...
		- `var A = array[0..5] of float`
	- In a name compatibility system which has no type and is not compatible with the Array1, Array2, Array3 types or anything else with the same structure but in a structural compatibility system it would be.
	- **Note**: In Modula-2 and Ada, formal parameters and actual parameters must have the same named type.
#### Expressions
- Are build from operators (which could be functions)
- and operands (arguments or parameters)
#### Operators
- Can be classified in many ways:
	1. Pre-defined (built-in) vs. User-Defined
	2. Unary/Monadic (one operand) vs. Binary/Dynadic (two operands)
	3. By position of the operator as prefix, infix, postfix.
- **Note**: Procedure rules are needed for infix notation only, not for prefix or postfix/
- **Note**: In most languages, unary + has no effect, but in Java it changes to char/short/byte to int
#### Overloading of Operators
- Much of this is built-in, for instance `a + b` could well work if a and b are of type cardinal, int, float, complex, and the variants of these long/short, etc.
- Ada allows 


**18.  _Type Compatibility, Type Chart_s, _Expressions and Assignments_**

**[10 per person]** a. Write code in a language that has enumeration types and test what kinds of operations are allowed on them and what kinds of silly or dangerous things are either allowed or forbidden. Report on your findings with code. (One possible example: If you have the type (mon, tue, wed) are increment and decrement allowed, or can you even just add a number to one of these? One such value to another? What if you increment the value wed? You can think of other issues I am sure. Two languages you could compare are C++ and C# (Do with a partner?? more than one partner?? Each partner hands it in on their assignment with the names of all the partners.)