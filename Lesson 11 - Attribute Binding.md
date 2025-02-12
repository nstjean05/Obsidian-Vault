#### Attributes and Binding
- All programs have entities with various attributes.
	- Name, type, storage, parameters, scope, etc.
- Specifying the nature and/or value of attributes is called binding.
	- Information placed in a descriptor for compile/load/run time.
- The binding time varies. It could be at the time of:
	- Language Definition (Built-in)
	- Language Implementation (Compiler maker- precision, etc.)
	- Program Translation (relative memory locations)
	- Link (Bodies of external functions)
	- Load (Actual static memory locations)
	- Run (Dynamic variable memory locations)
- **Note**: A language translator stores bindings in a symbol table which is later used by the linker.
	- It adds more bindings and passes a version forward to the finished application, which is used at run time to detect run-time errors and/or by embedded debugging code (usually removed for end-user version)
#### Issues and Attributes for Binding
##### e.g. Names
- Length limitation, case sensitivity, permitted characters.
	- Especially for "specials" like % * _ etc.
- Must distinguish among reserved words, standard definitions, and user-defined names.
##### Style Notes
- There are older and newer methods for naming.
	- Old: **my variable** **or my_variable** (Allowed in old Fortran)
	- New: myVariable