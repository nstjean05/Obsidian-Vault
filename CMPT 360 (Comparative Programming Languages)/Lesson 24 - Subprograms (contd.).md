#complete  
### Terminology (contd.)
7. The local referencing environment.
	- Old FORTRAN
		- Memory allocation is done by the loader, and everything is static.
		- Result: Recursion is impossible as instances of subprograms with different memory on a recursive call cannot be created dynamically.
	- All Algol-descended languages (+, if specified, Fortran 90+)
		- On every call to a procedure/function on activation record (AR) is created (stack dynamic) for parameters, local variables, return address, and the previous stack pointer value.
### Parameter Passing Semantics
- A given subprogram parameter may have one or more of the following semantics.
##### Copy-In or Passy-by-Values
- Semantics: The data in the actualy parameter is copied to the memory allocated to the formal parameter.
##### Copy-Out or Pass-by-ValueResult
- Semantics: The data in the local (actual parameter) is copied back to the memory allocated to the actual parameter.
##### Copy-In-Copy-Out
- Semantics: both Copy-In and Copy-Out
- **Note**: All of the above require time to do te copy and local (stack) memory to hold the copy. This can be a problem for, say, large arrays or other data structures.
##### Variable or Pass-by-Reference
- Semantics: The formal parameter is a pointer whose value is assigned the address of the actual parameter. Any changes made locally are therefore automatically reflected immediately in the global entity.
- The only memory required is for a pointer (reference)
- No copying is done.
- The effect is the same as copy-in-copy-out, but with less time and space.
- Objects and procedures are usually passed this way automatically.
- C passes all arrays automatically as referenced
	- Specific dereferencing is required inside the function to refer to the item.
	- A reference parameter is tagged (apart from arrays) in C with 8
- A reference parameter is tagged with VAR in the literal languages and arrays are not automatically variable parameters (pointers).
##### Pass-by-Name
- Used in some older languages.
- Semantics: The actual parameter is textually substituted for the formal name at the time the subprogram is called (late binding).
- **Note**: This means that each use of the name on reading its value could access a different value if the item has been changed, and depending on the actual name, results could be rather strange.
### General Parameters
- In Modula-2 R10 `CONST` parameters are immutable.
- In Ada `in` parameters are immutable.
	- `out` parameters are mutable but not readable
	- `in out` parameters are read/write with copy-in-copy-out semantics
- In C++ a reference parameter can be made immutable with a `CONST` prefix
	- e.g. `void doFunky(const int&p, int&q)`
	- has an in reference parameter and in in-out reference parameter (both reference semantics)
### Type Checking of Parameters
- Does the type of the actual parameter have to match that of the formal parameter and if so what are the exact rules for "match"?
- Strongly typed languages require an exact (by name) match all or most of the time. Weakly typed languages might not check this at all.
- C had the syntax:
```C
float cos(x)
float x
{
...
}
```
- Which defined x as float for the function scope, but did not check whether the actual parameters matched.
- ANSI C & C++ use prototypes (header definitions)
```C++
float cos(float x)
{
...
}
```
- That do check the type and either:
	- Do a data conversion if possible OR
	- Generate a syntax error otherwise.
	- Also the prototype `printf(const char*,...)` takes an indefinite number of parameters after the initial character string and they may be of any type.
### Implementation of Parameter Passing Strategies
##### Pass-by-Value
- Is implemented by copying the data into the procedure's activation record on the stack.
- This is usually mutable but unless there is copy-out, the altered values are lost on function/procedure exit.
##### Pass-by-Reference
- Is implemented by pointers, which in most languages are *implicitly* dereferenced.
	- e.g. if the parameter name is `p`, you refer to its data as `p`, rather than `*p` or `p AND`.
##### Pass-by-Name
- Is implemented with a code fragment (a *thunk*) that evaluates the name on each instance.
##### Asides
1. Arrays present their own problems and often get special treatment (e.g. automatic reference in C)
2. Passing of procedure/function names as parameters may or may not be allowed and could get special treatment.
3. In Java there are primitive types (byte, short, int, long, float, double, boolean, char), which are passed by a value.
	- Everything else is non-primitive and passed by reference.
4. Python is similar but has no primitive types, so everything is a reference.
	- As such, since these are the same rules as for assignment, it can be called pass-by-assignment, but the semantics are *reference*.

**24. _Subprograms_ (2) The Local Referencing Environment & Parameters**

**[3]** a. Argue for or against the inclusion of the value/type void in C
- The void function provides a way for programmers to create functions, without the need to return a value. 

**[5]** b. Explain in your own words the following succinct saying: "in C everything is a function and in Modula-2 everything is a procedure."

**[5]** c. What are the arguments for and against allowing a program to define additional definitions for existing operators such as is allowed in Python. Is this user-defined operator overloading a good idea or a bad one? Support