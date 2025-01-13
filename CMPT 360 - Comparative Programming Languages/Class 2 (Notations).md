##### Appropriateness
- Why am I using this language for this problem?
- Is it highly important that this program is readable?
	- Maintenance
	- Lessens how cryptic the code is
- How simple is this code to understand?
	- Can someone easily learn an use it?
##### Orthogonality
- A class of syntax which...
	- has only one meaning in every context.
	- is always used in the same way in that context.
	- can, however, be overdone.
##### Control Statements
- Selection (IF, CASE)
- Repetition (WHILE, REPEAT, LOOP, FOR)
- Doesn't have GOTO
##### Data Types
- Does the type distinguish between a whole/float type?
- Is Boolean a first-class citizen?
	- Is it T/F value actually assigned, or simply depicted as such?
- Does the program have...
	- enumerations?
	- ranges?
	- pointer types?
	- class types?
##### Structured Types
- Arrays (indexing)
- Records (field selection)
- Sets (elements, operations)
##### Abstract Data Types
- How?
- Where (library)?
- Relationship between the library and built-in types?
	- Are the lib types treated differently?
- Blueprints?
	- Ex. If you want to def a numeric type, maybe there is a blueprint that shows how a numeric type must be applied within the program, and you must follow that blueprint.
##### Composition
- Sequence, Selection, and Repetition are the 3 primary paradigms.
- Composition is the 4th paradigm, which explains how to package the program.
- Is there a distinct separation between procedures and functions?
##### Syntax
- Lexis
	- What characters are legal to type?
- Rules for identifiers
	- Legal first, subsequent symbols.
- Reserved words and symbols
	- How many?
	- Are they readable?
- Standard Identifiers
- Macros
- Association between form and meaning?
	- What do *this++* or *grep* mean?
##### Writability
- Must be considered within the problem domain.
	- For example, it would be foolish to write a business app in Fortran.
- Does a highly writable language diminish its readability?
- Complex and/or non-orthogonal notations are hard to write in.
- How expressible is the software?
	- Is there notation for complex operations (e.g. matrix inversion)?
##### Reliability
- Type safety checking?
	- ex. *4 + 6.5*
	- Sometime you can combine an int and a floa


