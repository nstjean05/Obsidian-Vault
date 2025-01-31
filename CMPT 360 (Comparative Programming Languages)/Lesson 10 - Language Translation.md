#### Language Translation
![[Pasted image 20250131081811.png]]
- Other options include:
	- Compile to another language and compile that.
	- Compile to virtual machine and interpret or compile that.
- **Note** that...
	1. Some Languages are better suited to one or the other.
	2. Some languages are more static, some are more dynamic.
#### Compiler Stages
1. Lexical Analyzer (Scanner)
	- Translate source into a sequence of attributed tokens.
	- e.g. identifier, assignment operator, expression.
	- Report on any use of illegal characters in context.
2. Syntax Analyzer (parser)
	- Examine the structure of token sequence against syntax rules.
	- Report missing tokens and/or incorrectly formed entities.
3. Semantic Analyzer (static)
	- Examines the static semantics
	- Report tiny things, like incompatible types, undeclared variables
	- Examines some of the dynamic semantics
	- Reports things like out-of-range errors (where possible)
4. Code Generator (.obj or intermediate code)
	- Produces the object code, including:
		- Code to check dynamic semantics.
- **Note**: Depending on the language and compilation strategy the code may need to be read and analyzed several times (passes).
#### Lexical Analysis
