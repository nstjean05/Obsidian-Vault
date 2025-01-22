## Syntax & Semantics Description
### The Issue:
- The program must be able to communicate to the compiler using rules for writing and reading program code (DWIM is never sufficient). Machine recognition is very literal.
### Vocabulary:
##### Syntax
- Refers to the form of a notation's programs, statements, and expressions. The module punctuation, spelling, and grammar - which must be exact.
- Rules for writing programs
- Form of correct statements
- Spelling, punctuation, grammar - exact
##### Semantics
- Refers to the meaning of the above - both at compile time (static) and at run time (dynamic) i.e. what is supposed to happen when syntax is used.
- Meaning of code
##### Syntax contd.
- You need an alphabet of legal symbols or characters
- Specified with lexical rules
- Valid combinations of characters are **lexenes**
- Groups of lexenes are called **tokens**
	- An **identifier token** could have many possible lexenes (valid character strings) such as "x", "y", "total", "count", etc.
- A set of **syntax rules** for the language specifies the correctly constructed strings for a **lexene** or a combination of lexenes that forms a sentence.
- A **program** is constructed from one or more sentences, again according to syntax rules.
	- This is presented bottom-up but designed top-down.
## Categories of Tokens
##### Reserved Words or Keywords
- Things that make up the program structure
- Cannot be reused
- e.g. loop, package, MODULE, etc.
##### Reserved Symbols
- Also cannot generally be re-used.
- May be user-overloadable.
- e.g.  ;  <=  +  etc.
##### Literals
- These are tokens whose name is an encoding of their value.
- NOTE: These are not the same thing as constants, contrary to popular teaching.
	- For instance, PI is a constant, whereas 3.14 is a value (literal).
- e.g. 4, 1.5, -2.3E46, "C", "Hello", TRUE, 3.4 + 2.7i, etc.
##### Identifiers
- A built-in or standard.
		- e.g. float, REAL, COMPLEX
	- Names of built-in types or values.
		- e.g. TRUE/FALSE
	- In some languages these are classified as reserved words.
- OR user defined names constructed per the language rules.
	- i.e. Employed for constants & variables.



