### What is a language (notation)?
- Formal notational systems for expressing problem solving abstractions in human and machine readable form.
- OR: Extended algebraic notational systems.
### Machine vs. Assembler vs. High Level Language
- Each has a different degree of legibility, and correlation with what the computer is told to do.
1. Even when writing assembler, one must know intimate details of the machine's hardware and/or firmware.
2. High level languages, especially if ISO standardized, are machine dependant.
3. Machine readability can be precisely defined, whereas human readability is an imprecise idea.
### Why Study Programming Notations?
- Increased ability to express abstractions of problems and their solutions.
- To best choose appropriate programming tools.
- Increased ability to learn new notations.
- To better understand implementation issues.
- To more efficiently use the tools you know.
- To know how and why notations are designed.
- To know when and why to accept a design.
- To create a language design.
### What are the problem solving domains?
##### Scientific
- Many computations, much use of arrays.
	- Fortran, APL, C++, Julia, Algol
##### Business
- Reports, computations in fixed-point numerals.
	- COBOL, RPG, C++, Delphi, Database proprietary languages, Application specific languages.
##### AI/Machine Learning
- Symbols other than numerals are manipulated, much use of lists.
	- Prolog, LISP, Scheme.
##### Systems Programming
- Continuous use, must access hardware, OS.
	- C, Modula-2, and their many derivatives.
##### Scripting
- Automating applications and workflows.
	- OS Shells, awk, tcl/tk, AppleScript, ECMAScrip (ISO std name for JavaScript), Perl, PHP & MySQL, Ruby.
##### Commercial Applications
- General Purposes.
	- C, C++, C#, Objective C, Swift, Java, Modula-2, Python.
##### Internet
- Web Programming.
	- Markup - HTML
	- Scripting/Database - PHP & MySQL
	- General Purpose - Java, C#
	- Scripting Languages
##### Embedded Systems
- Real time applications, such as robotics.
	- Modula-2, Ada, C++, R, Specialty Languages.
##### Application Specific Languages
- Scripting applications: spreadsheets, database managers.
	- VBA, DataBase Languages (Pascal, Modula-2, C), Specialty Languages.
##### Other
- There are many, many other:
	- Languages
	- Programming Environments
	- Libraries of pre-written code that can be called
	- Applications or OS specific APIs, etc.


***Intro and problem domains***

**[3] a. Is the capacity for thought influenced by language? Explain.**
- The capacity for thought is absolutely influenced by language, in a wide variety of areas. Fundamentally, learning language allows for the clear expression and communication of thought to others, incentivizing individuals to give their thoughts structure. This can expand the capacity for thought, by making it easier to build off of cemented ideas, but may also limit thoughts to what seems more reasonable/communicable. In the context of programming, learning languages can be highly useful in expanding the capacity for thought, especially in giving structure to thinking about abstract ideas/concepts.

**[3] b. Argue for the idea of a single language for all programming domains.**
- A single language would be the best way to solve problems across any domains, as the advantages of scale would outweigh any maleffects. The primary drawback of having a single (standardized) language would be that for different problems, it would have different levels of efficiency. For instance, it would be exceptionally inefficient for a systems language in the domain of web development. Yet, this drawback would be minimized greatly by the scale of use of this language. Given the massive amount of programmers working on and with the single language, even non-trivial problems can be solved rapidly. As example of an impossible feat solved by an influx of resources, less than 10 years after the first plants and animals went to space, humans were walking on the moon. In the same way, any immediate and insurmountable problem would be solved with the trillions of dollars at the disposal of major tech companies and powerful governments. Additionally, consolidating programming to a single language would make learning it far more accessible to more people, and would help to expand the bounds of the language itself. Just as English has evolved to suit the needs of people outside of England, this programming language's diction would expand to meet its new demands.

**[3] c. Argue against the idea of a single language for all programming domains.**
- A single language with mandated use in all programming domains would be disastrous and wasteful. Different languages have surfaced over time to suit the needs of the people in that time and place. As new innovations occur, it is optimal for new languages to be written, as they will function in their domain better than any other could. Additionally, new languages avoid the problem which many old ones succumb to- bloating. A single language needs to give support to both old and new innovations, regardless of how much the old will slow down the new. While it would be great to give up old, roundabout features, what happens to archaic yet important machines (for instance, medical devices) which run utilizing those features? Imagine if when the mass-adoption of cell phones occurred, all fax machines were bricked. This would lead to breakdowns in communication between many crucial networks. Therefore, it is important to have a wide variety of languages which can borrow from the past, but shed the deadweight in favour of new innovations.

**[3] d. From among the languages you have used, which statement is the hardest to read and understand, and why?**
- The hardest statement to understand, that I wrote in C++, was the below. This was a line that I had difficulty in writing, and then had difficult understanding when I went back to read it later. I think it would have helped a lot if my comment had been useful, rather than just stating what the line does. Another complicated part of it is that this was my first implementation of a clock, and when re-reading the code it isn't immediately obvious what *stead_clock* indicates. This line of code is dense in general, and deals with some interconnected concepts which together add complexity.
```C++
time_point<steady_clock> endTime = runLimit * 1s + start; //calculate end time
```

**[3] e. Who was Augusta, the Countess of Lovelace? What programming language is named after her and why?**
- Augusta Byron, daughter of poet Lord Byron, is commonly known as the first computer programmer. She began as a mathematician with interest in mechanics, but transitioned her research to mechanical machines. Lovelace later collaborated with mathematician Charles Babbage, on a project building the Analytical Machine. During her time working on the project, she developed the first computer program in an effort to calculate Bernoulli numbers. The language named for her was developed for the US DoD, in an effort to have a single, standardized language for embedded systems.