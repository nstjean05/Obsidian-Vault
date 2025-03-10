### Subprograms
- Composition mechanisms which are based on a call-return model.
#### Principle
- One entry point (Fortran could have multiple ones)
- Alternative: Call-return is not accurate in a concurrent system.
### Terminology
1. A subprogram **definition** describes its...
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
	- Generally, this means that 