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
	- Freezing the binding to create symbolic constants.
	- An expression at run-time market static
	- A parameter market CONST or static that is frozen inside the procedure/function
- And of course Literals have a manifest value --  their name encodes their value.
- **Issue**: What is a variable's value after declaration but before initialization or assignment?
- **Answers**:
	- Undefined
	- Defined to be 0, nil, empty (some default value)
	- Given a default value in the declaration syntax
	- Defined as uninitialized and therefore unreadable (clean but costly)
##### Storage Binding
- This may be determined or allocated...
###### Statically
- At compile time.
- Globally accessible.
- Able to survive execution? (history sensitive)
	- In Fortran all variables are static and global
- **Note**: We refer to here to the relative memory location, not the physical one determined by the loader.
###### Stack-Dynamic
- When the containing block activates.
- Applies to procedure/function parameters and local variables in all Algol-like languages
- **Note**: This facility allows recursion, because each recursive call sets up a new lot of variables.
###### Explicit Heap Dynamic
- Manual via pointers
- Managed by NEW/DISPOSE procedures at run-time
- Potential problems with aliases, garbage
###### Implicit Heap-Dynamic
- Bound anew at every assignment
- Often done automatically for strings
	- old BASIC, Perl, JavaScript

**11.  _Attribute Binding_**

**[3]** a. Which of the following is most readable and why? SumOfSales, sum_of_sales, SUMOFSALES
- I think that the most readable of these is sum_of_sales, as the underscores create spacing which means my brain didn't need to parse the words apart. After that, I would say that SumOfSales is somewhat readable, as is has capitals to denote a new word. However, its lack of camelcase was a bit unintuitive. Finally, SUMOFSALES is the least readable due to its capital-uniformity.

**[3]** b. Look up and explicate the meaning of LL(1) grammars.
- LL(1) grammar is a method of structuring context-free grammars. In the case of LL(1), the entry is scanned left to right, and only one character at a time by the analyser. Additionally, it produces a leftmost derivation, or one which works best with a YACC parser.
https://www.csd.uwo.ca/~mmorenom/CS447/Lectures/Syntax.html/node14.html
https://link.springer.com/content/pdf/10.1007/3540069585_47.pdf

**[3]** c. Describe as many circumstances as you can under which the memory location of an entity is bound dynamically.
- Dynamic memory allocation refers to a method of memory allocation which is done at runtime, and memory is allotted according to when the program requests it. For instance whenever a variable is created in Java, a location is automatically found for it to be stored. This location may change throughout the course of the program, as more is computed. The advantage of this (relative to static allocation) is that variables or structures can be assigned more flexibly, especially in instances where values are not known before the program begins, as this can lead to highly inefficient allocation.
https://www.geeksforgeeks.org/what-is-dynamic-memory-allocation/