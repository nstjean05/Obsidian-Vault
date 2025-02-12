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
	- New: **myVariable** (Camel style of studley caps)
- Some languages have context-sensitive keywords (e.g. Fortran)
	- Sometimes these are reserved words, sometimes standard identifiers.
	- This is acceptable if the context is clean, but it is non-orthogonal.
- Sometimes an identifier may be used in a dual role.
	- e.g. ADDRESS could be both a data type and a procedure name, which is called a Schrödinger Token and is also non-orthogonal. (Modula-2 R16)
#### Variables
- For languages to which this applied, based on cell location and value.
#### Attributes
##### Name
- Identifiers one for compiler use --> memory location at run time
- Dynamic variables referred to with notation such as 'a^' are nameless in a sense as 'a^' is a *reference* and not a name.
##### Address
- This is a memory location or a l-value (what is evaluated on the left-hand-side of an assignment)
- A given name such as *loopcount* may have different addresses in different parts (scopes) of the program
- Aliases