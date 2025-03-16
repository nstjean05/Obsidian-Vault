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
- Semantic