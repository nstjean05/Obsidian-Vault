#incomplete 
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
- 