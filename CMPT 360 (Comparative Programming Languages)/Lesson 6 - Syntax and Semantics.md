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
##### Literals 2
- Most notations have a "rule of longest substring" to determine where one string ends and another may begin, which means spaces matter. Therefore:
	1. beginwhile is a user identifier
	2. begin while is two reserved words.
- However, some langauges do forbid using a reserved word as a part of an identifier and would not allow case 1.
- Additionally, FORTRAN determined meaning in part from position, not spaces.
	1. DO 99 I = 5.10 means assign the value 5.10 to DO99I
	2. DO 99 I = 5,10 means for I = 5 to 10 do, with the spaces being irrelevant
- Moreover, FORTRAN had no reserved words so REPEAT = 7 is a legal assignment. Yikes!
- Python also derives meaning from spaces and the indentation on each line.
##### Language Definition
- Based on:
	- **Formal:**
		- Rules for a compiler to recognize correct strings.
			- i.e. The compiler uses rules in **syntax analysis**.
	- **Informal:**
		- Models or examples to illustrate correct string patterns.
			- i.e. How-to recipes in a textbook.



**6. M _Syntax and Semantics_** 

**[5]** a. Look up VDM-SL and write two paragraphs on it.
The Vienna Development Method Specification Language (VDM-SL) is a guide for creating programming languages built on the fundamentals of the Vienna Development Method. This is one of the things that makes it unique, as "VDM-SL is a language for specification as well as development" (Dawes, 1991). 