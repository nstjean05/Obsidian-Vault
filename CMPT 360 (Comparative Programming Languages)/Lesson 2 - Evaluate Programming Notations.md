#complete
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
	- Sometimes you can combine an int and a float automatically, but sometimes you would need to define the new number as a float.
- Exceptions
	- When everything goes wrong, what happens?
	- Some languages stop when an exception is reached, and allow you to fix it.
- Pointer Safety
	- Can a given memory cell have more than one pointer reference?
	- Don't have 2 pointers back to the same location!
##### Costs
- Many of these aspects trade off with one another in their costs/
	- Planning
	- Coding
	- Compilation/linking
	- Execution
	- Testing
	- Maintenance
- Read/writability affect reliability and maintainability costs.
##### Msc. Evaluation Criteria
- Portability
	- Can applications developed for one platform be easily ported to others?
- Generality
	- Is it a notation?
		- Specific to one application or domain?
		- Applicable to a wide range of applications?
- Is it defined fully and unambiguously?
- Are compilers/interpreters/tools/code libraries widely available?

***2. Evaluating Notations***

**[4] a. Discuss readability vs. writability. What is each and how do they sometimes trade off? Which is more important, and why?**
	Readability and writability are both critical components of language design, and each greatly contribute to how a user interacts with the language. Readability refers to how easily text can be read. Is the code as natural to read as your native tongue, or does it require the effort and back-tracking of a language you are learning? Writability, on the other hand, refers to the efficiency and ease of which a program can be written. These two variables often have a give and take relationship. For example, a highly orthogonal language is generally easier to write in, as it allows for the author to use many different combinations to achieve a single outcome. However, this can decrease readability, as a reader must then become familiar with orders of magnitude more combinations of factors. Depending on the use case of the language, either one of these can be prioritized. If a large quantity of code must be written, and by a relatively small and specialized group of people, then writability may be prioritized (e.g. assembly languages). However, if a large amount of people need to be able to frequently access or learn to write it a certain language, then it would likely be more efficient to emphasize readability (e.g. open source projects or large companies). Regardless, it is important for any language to be aware and accommodating of both.

**[4]b. Many languages distinguish between upper and lower case letters in user-defined names. What are the pros and cons of this?**
	Distinguishing between upper and lower case letters is done for several reasons, but the most evident reason is probably that many written languages already distinguish between the two. Allowing for the difference to also be made in code enhances both read and writability- it allows for more variations to be written, and allows the code to be read in a more natural way. A primary reason that some languages became insensitive was that early computers could only accept so many variations, and insensitivity was a relatively simple way to narrow down inputs. Additionally, in-distinguishing between cases can allow for fewer errors to be made, or can help in simplifying grammar. However, in modern-day software development, the pros of case sensitivity generally outweigh the cons.
	
**[3]c. How do type declarations affect the readability of programs in languages that require them (not all do).**
	Type declarations has both benefits and detractions to the readability of a program. On the pro side, they can make it very obvious what type a given variable is. This can help with tracking what is happening to values throughout a program, and can enhance the structure of the code. However, adding in type declarations can also serve to clutter a program, and can make it difficult for different types to interact with one another.
	
**[4]d. Some languages have two kinds of comments--one with an open comment marker that extends to the end of a line, and another with both open and close delimiters that can extend over many lines. What are the advantages and disadvantages of each, of having both?**
	Single-line comments are very useful, as they allow for short remarks to be made throughout a file without adding clutter. They remain in-line with the code, and allow for increased readability and flow. Sometimes these may be overused, and can be difficult to remove in bulk. Open/close comments also have their place, as they allow larger portions of text to be segmented apart. This can allow for natural-language text to be written, or can help with writing code/testing as portions can quickly be effectively removed before running the program. Yet, this is not very efficient for short comments, as it requires more text to be written, and the open/close ends to be tracked more closely. It is useful for many programming languages to have both kinds, as each generally covers the others weaknesses.
