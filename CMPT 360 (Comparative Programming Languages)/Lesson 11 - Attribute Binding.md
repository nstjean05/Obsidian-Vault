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
- Aliases (two names for the same memory)
	- These could be two pointers to the same memory, or variable/reference parameters.
##### Type
- This specifies:
	- The range of values that such items can take on.
	- The permissible operation on it, e.g. type REAL may allow *+ - * / max min* (at least implicitly)
	- Some operations associated with a type are...
		- ...built-in to the language
		- ...imported from one or more libraries
##### Value
- This is the coded/stored representation
- Is usually thought of as occupying an abstract memory cell of one+ bytes or words
	- Abstract because it is a program concept not a physical one.
- Is called an r-value (evaluated on rhs of assignment)
##### Scope
- The range of program instructions over which the entity is known (visible, useable)
- This is **not** the scope of the name --  several  entities may have the same name but exist in different scopes.
	- e.g. variables defined as either function parameters OR locally to a function
#### Binding of Attributes
- Can be:
	- Static, before run-time, unchanged thereafter.
	- Dynamic, attributed/changed during run-time
##### Type Binding
- Generally static, except a few cases.
	- Fortran, PL/1, BASIC first use is type declaration.
	- JavaScript, PHP, APL type is dynamic per current value.
	- Fortran has default implicit type depending on first letter of the identifier.
		- I,J,K,L,M --> integer, T to Z --> real
	- ML (and other) permit type to be inferred.
	- Perl
		- First letter $ --> scalar @ array
	- BASIC
		- First letter $ --> string
				   % --> integer
		- ELSE real
	- And there are many other variations on the theme.
##### Value Binding
- Variables, usually dynamic (via assignment) but some allow:
