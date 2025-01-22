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
	

**[10] b. Now, using a language with which you are already familiar, evaluate it by these criteria.**

**[8] c. Explain what the following acronyms mean and what the entity behind them do: ECMA (now Ecma), ISO, CSA, BSI, SCC, ASCII, IEEE, ACM**

**[3] d. Some languages (e.g. Pascal, Modula-2) use the semicolon to separate statements, whereas others (e.g. Java) use them to terminate statements. Which of these in your opinion is more natural and least likely to produce errors? Support your answer.**



Criteria:
1. Readability
	1. Simplicity
	2. Orthogonality
	3. Data Types
	4. Syntax Design
2. Writability
	1. Simplicity and Orthogonality
	2. Expressivity
3. Reliability
	1. Type Checking
	2. Exception Handling
	3. Aliasing
	4. Read and Writability
4. Cost
5. 
