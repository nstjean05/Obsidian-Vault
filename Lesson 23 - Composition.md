### Subprograms
- Composition mechanisms which are based on a call-return model.
#### Principle
- One entry point (Fortran could have multiple ones)
- Alternative: Call-return is not accurate in a concurrent system.
### Terminology
##### 1. A subprogram **definition** describes its...
	- Interface and actions using a header as its first line to provide, as applicable
	- Formal parameters and types
	- return value types
2. A **call** or **invocation** is a request to transfer control to the subprogram
	- Whereupon it becomes **active**
	- Until is **returns** control to the calling unit
3. Some languages allow **forward** or **external** definitions.
	- Which promise a later (or external) declaration, including the code body
	- Needed for single-pass compilers
	- Forward definitions are not declarations
4. Actual parameters that **match** the formal ones in the definition must be applied when the subprogram is called.
	- Generally, this means that formal parameters are dummies-- not bound to storage until run time.
	- The meaning of "match" varies from...
		- The order, number, and exact type
		- None of these being necessary at all
		- e.g. `float doit(float param1, int param2 = 5)` can be called by `doit(3.7)` (C++)
	- As in other circumstances, C languages put the type before the entity name, whereas in literary languages it is often opposite.
	- In some languages the latter n parameters can be defaulted and omitted in the call.
	- Some do not check type mixing.
	- Some (Ada, Python, VB) allow parameter ordering to be changed at call time by listing actual parameters and designating where they are to be bound
	- Some (C, C++, Perl, JavaScript) allow parameters to be left out even if there are no defaults. It is up to the programmer to decide if this makes sense.
5. Categories of subprograms
		a. **Procedures**