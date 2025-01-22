#### vonNeumann Architecture
- 4 Fundamental Principles of the architecture
	- Binary coding is fundamental to all languages, as this is how computers store information.
	- Stored programs in memory separate from the CPU
	- Instructions and data fetched from memory to CPU
	- Sequential execution
- **Not all languages are vonNeumann** (e.g. Lisp, Scheme), although they have to reside on vonNeumann architecture.
- Variables represent memory locations
- Assignment statements model moving data.
	- Called *piping*
- Efficient repetition statements are available.
- Memory stored on the CPU is processed much more rapidly that that which is not.
- The fetch-and-execute loop.
	- Loop
		- Fetch the instruction pointed to by the program counter.
		- Increment the counter to point to the next instruction.
		- Decode the instruction (into microcodes which are only used by the CPU).
		- Execute the instruction.
	- End
- Note that this loop executes indefinitely, until interrupted or specifically exited.
#### Basic Programming Paradigms
1. Sequence: Statements executing in the order presented.
2. Selection (if..then..else, case, select)
3. Repetition (for, whole, repeat, loop)
4. Composition (abstracting into modules, programs, procedures, productions, functions, blocks, that can be called as a unit- usually by the name)
- There are additional paradigms which extrapolate on these.
- Parallelism
	- Multiple processors and/or multiple processes.
	- Requires language facilities.
	- This aspect of programming is immature.
#### Methodologies
- Pre-1960s
	- Simple applications
	- Machine efficiency is a major issue
	- People issues starting to become important
- Late-1960s
	- Block structured programming
	- Top-down design and stepwise refinement of code
- Late-1970s
	- Process orientations transitions to data orientation and ADTs
- 1980s
	- Data-class orientation transitions to OO programming
		- This adds inheritance and polymorphism
	- Process orientation --> Concurrency
		- Allows for more processing to occur at once
- 2000s
	- Greater emphasis on safety, security & reliability, requiring new workflows.
#### Design Tradeoffs
- Design Time ---- Coding and Testing Time
- Writeability ---- Readability
- Writing Time ---- Running Time
- Reliability ---- Cost
- Present and future efficiency ---- Installed Base
#### Language Categories
- Imperative
	- Feature variables, assignment statements, and iteration
	- Include ones that support OO programming
	- Include scripting and the "visual" languages
	- Ex. C, Java, Perl, JS, etc.
- Functional
	- Computations are solely done by applying functions
	- Ex. LISP, Scheme, ML, F#
- Logic
	- These are rule-based
	- Ex. Prolog
- Markup/Programming Hybrid
	- Markup languages extended to support some programming
	- Ex. JSTL, XSLT
## Programming Environment: Virtual Machine
#### Language Translation Strategies: Language May Be
- Compiled to CPU machine language (macroinstructions)
	- At run-time translated by the CPU to microinstructions
	- Target: Commercial applications where speed is an issue.
- Compiled to executable microinstructions (even faster; rare)
- Interpreted during run time into microinstructions (slower)
	- Target: small applications where speed is not an issue.
- Compiled to VM instructions which are either:
	- Interpreted into microinstructions at run time (hybrid)
	- JIT (Just InTime) compiled at run time, then executed
###### Some languages are...
- Always compiled (most imperative languages, except Java)
- Always interpreted (most other languages)
- May exist in either world
#### The Compilation Process
1. In the programming environment, the developer creates a text file.
2. A pre-processor may translate macro directives in this text file to include other code as though it were part of the text.
3. The compiler produces and object file and a symbol file for the linker to find and reconcile other object files referenced by the program.
4. The linker ties this together with existing code libraries. to produce an executable file.
5. The run time system of the OS executes the latter file.
###### Variants of the Code Production Process
- **Pure interpretation** uses the text file at run time to generate instructions one at a time on the fly.
- Hybrid systems use a compiler to create an intermediate code that is in turn interpreted by a VM at run time. Programs can be ported onto a new platform by porting the VM only.
- JIT systems are simply delayed compilers.
#### Internal Performance Issues
- The CPU and memory talk to each other on a pipeline which is speed limited.
- Code execution is much faster than the pipeline, and this limits the overall execution speed.
	- Known as the *vonNeumann Bottleneck*
- Multiple cores, bulk code loading into a CPU cache, and execution prediction are some strategies used to overcome said bottleneck.











**3.** **_Design Influences_**

**[5]** **a. By what criteria are programming languages judged? Name at least five & explain.**
	There are many ways that a programming language can and must be judged. These criteria allow for languages to be consciously optimized for different means. The first criterion is simplicity- the less constructs the language has, the simpler it is. A language must find the balance between having good support for a variety of functions, but not adding so many the language becomes bloated.
	Another criteria is that of syntax design. This is strongly linked to simplicity, as this is the mode through which the language is constructed. It is important to evaluate, for instance, what syntax a language reserves, and how the language's form serves to enhance its use-case.
	Abstraction is a method of evaluation which focuses on how data can be hidden, so that the code can be simplified. How abstractions can be implemented will greatly effect the efficiency of the language and its programs.
	A fourth pillar criteria is that of type checking. Through this, the program is verified to make sure that the types being manipulated are in alignment. If this is not checked, then significant errors can be made (e.g. a float type being used when int was expected). However, it is also very time consuming for every parameter to be type checked, so you can evaluate the program based on how efficiently/when they are checked.
	Finally, exception handling is another method of evaluating a programming language. It is highly important for the reliability of a program that errors are caught and dealt with, or else notified to the programmer. Yet, the absence of exception handling can allow for a more efficient program, and can decrease the amount of convoluted code. Each of these criteria are critical in the evaluation of a programming language, and which language is optimal for a given application.

**[10] b. Now, using a language with which you are already familiar, evaluate it by these criteria.**
	Python
	1. Simplicity
		Simplicity is one of the areas where Python thrives. It takes care of garbage collection, and has a flow similar to English, making it really great for teaching applications. However, it balances this simplicity out with its support for object and procedurally oriented programming.
	2. Syntax Design
		Python has a syntactical design which is relatively light in terms of how many words it has reserved, especially relative to languages like C++. This means that there is less for the programmer to memorize, and allows for less limitations on what can be done with each word. Python also has relatively loose form, in that there is nothing to denote the end of a line, and not a great deal of sentence structure or extra characters to denote it.
	3. Abstraction
		Python has some support for abstraction, as it is somewhat object-oriented. Additional functions can be written to simplify and partition the code. Python is relatively slow to compile when more abstraction is used, meaning that if your program hinges on performance, this may not be the way to go.
	4. Type Checking
		Python has support for type checking, to varying degrees of success. Its compile-time type checking can be on-par with other languages, but its runtime checking has similar detractions to abstraction- it can be rather slow.
	5. Exception Handling
		This is a great advantage of using Python, as its exception handling is very straightforward and effective. There are a number of keywords, including try, except, and finally, which serve to make Python's handling effective and versatile. However, it again falls victim to the issue of speed, as utilizing thorough exceptions can deteriorate performance greatly.

**[8] c. Explain what the following acronyms mean and what the entity behind them do: ECMA (now Ecma), ISO, CSA, BSI, SCC, ASCII, IEEE, ACM**
1. Ecma
	The European Computer Manufacturers Association is an organization which organizes technical standards, primarily in the space of communications technologies.
2. ISO
	The International Organization for Standardization develops standards for a very wide variety of items.
3. CSA
	Canadian Standards Association, which creates standards for many different industries, but with a focus on the Canadian geopolitical area.
4. SCC
	The Standards Council of Canada once again focuses on Canadian standards, with the addition of backing by the Canadian government, and representing Canada in various international standards organizations.
5. ASCII
	The American Standard Code for Information interchange is a standard for how numeric codes represent different textual characters.
7. IEEE
	The Institute of Electrical and Electronics Engineers creates standards in various engineering fields, and also regulates the title of 'Engineer' in Canada.
8. ACM
	The Association for Computing Machinery is an organization which works to build the community and discourse between/around computer scientists.
	
	
**[3] d. Some languages (e.g. Pascal, Modula-2) use the semicolon to separate statements, whereas others (e.g. Java) use them to terminate statements. Which of these in your opinion is more natural and least likely to produce errors? Support your answer.**
I think that terminator statements are much more natural, as well as less likely to produce errors. Guaranteeing that there is a semicolon after every line makes it simpler when going back and changing code, as there is no concern about accidentally adding/excepting a semicolon. It also increases readability, as now there is much less attention to be paid to whether a given line needs a semicolon.

- Simplicity
- Orthogonality
- Data Types
- Syntax Design
- Abstraction
- Expressivity
- Type Checking
- Exception Handling
- Restricted Aliasing

