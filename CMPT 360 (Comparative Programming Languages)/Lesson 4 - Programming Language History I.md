#complete
## Pre-History
- Blaise Pascal
- Leibniz
- Charles Babbage 1830-1840
	- The difference engine
	- the first programmer: Ada, Countess Lovelace
- The Jacquard Loom and its punched cards
## Early Modern Era
0. Plankalkul (Zuse) 1945
	- A prototype language
1. Fortran 54-57 (Backus--IBM)
	- Later WatFIV, Fortran 77, and Fortran 90+ (ISO)
	- Scientific work
2. COBOL 59-60 (Admiral Hopper -- USN)
	- Business
3. ALGOL 58-60
	- Zurich
	- Block Structure
	- Formal Definition in BNF (a metalanguage)
	- Heavily influenced everything after
#### For Symbolic Manipulation (Functional or Applicative)
4. LISP 56-62
	- John McCarthy MIT 1958
	- non VonNeumann
	- No variables, assignments, or goto
	- now Common Lisp
	- Has some compiled versions
5. APL 56-60 (Iverson)
	- Operator rich
	- Needs a special keyboard
6. SNOBOL 60-62 (Griswald - Bell Labs)
	- StriNg Oriented symBOLic Language
	- A dynamic language-- interpreted not compiled
7. PL/1 63-74 IBM (The 'All in one language')
	- Borrowed from everything prior
	- Tried to combine COBOL, FORTRAN, LISP
	- Exception handling
	- Primitive multitasking
	- Large; many previously untried features
	- A temporary success in academia
	- Too large to learn properly
#### Late 60s ALGOL Successors
8. ALGOL-68 (Committee effort)
	- Like PL/1 in being feature-rich (bloated)
	- Very orthogonal
9. ALGOL-W (Wirth & Hoare) (late 60s)
	- Wirth's reaction to ALGOL-68
10. SIMULA-67 (Nygaard & Dahl -- Oslo)
	- From SIMULA-1 (62-64)
	- Includes ALGOL-67
	- To solve simulation problems
	- Some parallelism possible
	- First language with CLASS; first OO language
11. Pascal (1971 Wirth)
	- Simple but powerful
	- Widely used in teaching
	- A huge impact to the late 1990s
	- Descendants include:
		- UCSD Pascal
		- ISO version
		- Object Pascal (Wirth on contract to Apple)
		- Turbo - Delphi environment
		- Ada, Modula-2, Modula-3, R10, Delphi, etc.
#### Hobbyist Languages
12. BASIC (1964 Kemeny & Kurttz @Dartmouth)
	- Simplified Fortran, also ALGOL influence
	- Line numbers to control sequence
	- Timeshared on large machines, built-in on the smaller
	- Early versions not well-defined
	- Limited control structures and data types
	- Integrated editing and interpreting
	- Descendants include:
		- ASCI BASIC, Real Basic (K&K), Future Basic
13. LOGO
	- Interactive Language for teaching children
	- Used in grade schools in the 70s-80s
## The Middle Ages
#### Results of the 70s Experiments
14. C (1972 Ritchie @Bell)
	- Another ALGOL 68 descendant
	- Designed for systems work
		- e.g. UNIX (later re-written in C)
	- A middle level language
	- Standardized by ANSI in 1989
15. Euclid (76-77 @UofT)
	- Pascal, extended with Modules
16. Mesa (76-79 -- Xerox)
	- Had concurrency facilities
17. Ada (1979 US DoD)(No longer mandated by the DoD)
	- Another Pascal replacement
	- Committee designed, large and complex
	- Published as Ada83
	- Largest design effort ever; took 4y to get a compiler
	- Completely specified, including libraries
	- got ISO version in 1990s as Ada95
18. Modula-2 (1997 -- Wirth @ETH; his reaction to ADA)
	- Much simpler than Ada, but as powerful
	- Replacement for Pascal
	- See PIM (Programming in Modula-2 4th ed.)
	- Teaching, real time (embedded) systems, general use
	- Influenced by MESA & Modula (a real time notation)
	- Got ISO version in the 1990s + generic & OO extensions
#### The early Modula-2 Descendants
19. Modula* (for parallel processing)
20. Modula-GM (used only at General Motors)
21. Modula-3 (Olivetti and DEC)
	- OO version
22. Oberon (Wirth)
	- Widely used in European universities
	- Has many versions including Component Pascal
	- Stripped down Modula-2; OO added in Oberon-2
	- Included an operating system & editor
	- Never completely specified
#### Other 1980s Experiments
23. Smalltalk (71-80 by Alan Kay @Xerox)
	- From SIMULA-67
	- An OO language, several implementations available
24. Scheme (75-77 Sussman & Stelle @MIT)
	- Variation of LISP
	- Used in several universities for beginners
25. PROLOG (1972, French)
	- Logic programming, AI an intelligent DB?
		- An attempt to use AI with a database
1. Eiffel (1985 Meyer)
	- Pascal-like OO language
		- & method of software construction
	- Smaller and simpler than C++
	- Was backed by some French companies & universities
## The Modern Era
#### Results of 90s Work
27. C++ (Bjarne Stroustrop, draft 1995)
	- C with OO, some deprications
	- Many new features, similarities with SIMULA
	- No garbage collection, programmer responsibility
	- Has generics (templates for ADTs)
	- More ISO compliant compilers now
	- Large, complex, non-orthogonal
	- Most deprecated features were never removed.
28. Modula-2 Extensions
- ISO committee added OO and generics 1998
29. J (Iversons)
	- An ASCII replacement of APL
	- No special keyboard needed; used in some colleges






**4.** **_Language History_**

In this section, basic factual matters from the overheads and lectures need to be known, as well as something of the history of once common languages such as Python, Java, C, C++, the .NET suite, Pascal, the Modula languages, and Ada all of which made important contributions to language design

**[3] a. What was the significance of the language** **Plankalkül?**
	This was the first computer/language to utilize loops, and a compiler. It made great advancements in its employment of data structures, implementing loops and the 'bit' data type. Plankalkül's programmer, Konrad Zuse, began working on it in 1943, and completed writing a paper about it in 1945.

**[3] b. Write a paragraph on the contributions to computing of Grace Hopper.**
	Grace Hopper was a pioneer in the computing sciences field. After completing a 4-year mathematics P.h.D. at Yale, she went on to be recruited to the U.S. navy. Hopper was one of the initial programmers to advocate for finding new ways to use a computer to code, and created the first compiler (called A-0). This system and its two descendants worked to translate pseudocode into various machine subprograms, which greatly saved on time and effort, as developers no longer needed to write in machine code. Continuing on this trend of revolutionizing the way programming languages are written, she introduced the concept that while math should be written in mathematical notation, software should be written in largely English statements. This went into the design of the COBOL language, which became the most used at the time, and introduced many revolutionary concepts.

**[5] c. Write a paragraph on the contributions to computing of Niklaus Wirth.**
	Suisse programmer Niklaus Wirth is known as the greatest programming language designer since the inception of computer science as a discipline. Along with the IFIP, he helped develop ALOL in the 60s. After seeing that the Federation's efforts would lead to bloated languages, Wirth went rogue, designing a series of widely used languages such as Pascal and Modula. Much of his improvements came from simplifying previously complicated ideas, making them much easier, efficient, more practical to use and teach.

**[3]** **d. Describe the concept of orthogonality in programming languages in your own words.**
	Orthogonality is the extent to which a programming language's features are able to combine with one another, allowing for varying degrees of combinations and complexity. A highly orthogonal language will have a small number of fundamental constructs, but a very large number of combinations, and a high degree of cross-compatibility/usage. Non-orthogonal languages have a much greater amount of structure, but don't have as much flexibility.

**[3] e. What are the arguments for and against the idea of a typeless language?**
	Typeless language refers to when a language doesn't have fixed types. This means that every piece of data used in the program is of the same type. The primary advantage of this is that it is much more simple to write and convert. There aren't errors between different values, as they are all compatible. However, this can also make obtuse scenarios more common, as there is little structure. Errors at runtime can actually be much more common, as they are not caught when writing or compiling the program.

**[3]** **f. Why do new scripting languages appear more frequently these days than do new compiled languages?**
	There are several key advantages of scripting languages that have led them to be more prevalent in recent years. The primary reason is that they are easier to work with. Since the average programmer doesn't need to worry about lower-level ideas like memory management, making them easier to learn. Additionally, scripting languages can be simpler to create. Since so many new, specialized use cases are being found, it is more likely that an easier program to create will be made to fit those slots.

