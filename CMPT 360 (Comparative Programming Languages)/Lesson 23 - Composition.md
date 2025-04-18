#complete
### Subprograms
- Composition mechanisms which are based on a call-return model.
#### Principle
- One entry point (Fortran could have multiple ones)
- Alternative: Call-return is not accurate in a concurrent system.
### Terminology
1. A subprogram **definition** describes its...
	- Interface and actions using a header as its first line to provide, as applicable
	- Formal parameters and types
	- return value types
2. A **call** or **invocation** is a request to transfer control to the subprogram
	- Whereupon it becomes **active**
	- Until is **returns** control to the calling unit
3. Some languages allow **forward** or **external** definitions.
	- Which promise a later (or external) declaration, including the code body
	- Needed for single-pass compilers
	- Forward definitions are not declarations
4. Actual parameters that **match** the formal ones in the definition must be applied when the subprogram is called.
	- Generally, this means that formal parameters are dummies-- not bound to storage until run time.
	- The meaning of "match" varies from...
		- The order, number, and exact type
		- None of these being necessary at all
		- e.g. `float doit(float param1, int param2 = 5)` can be called by `doit(3.7)` (C++)
	- As in other circumstances, C languages put the type before the entity name, whereas in literary languages it is often opposite.
	- In some languages the latter n parameters can be defaulted and omitted in the call.
	- Some do not check type mixing.
	- Some (Ada, Python, VB) allow parameter ordering to be changed at call time by listing actual parameters and designating where they are to be bound
	- Some (C, C++, Perl, JavaScript) allow parameters to be left out even if there are no defaults. It is up to the programmer to decide if this makes sense.
5. Categories of subprograms
	a. **Procedures**
	- These define new statements or commands, but can also...
		- modify global variables
		- "Reburn" referenced values (variable parameters)
	b. **Functions**
	- These are modelled on mathematical functions (ex. f(x,y)) and if done properly this means they...
		- Return a value of a specified type to an expression
		- Modify no state themselves
		- Are used to define new operations
		- Overload an operator (perhaps)
	- Note:
		- In C, C++, there are only functions; a procedure is a function whose return type is VOID.
		- In Modula-2 and Ada there are only procedures; a function is a procedure with a return value. One *may* end a proper procedure with a a bare RETURN, but one *must* end a function procedure with `RETURN<value>`
		- Other langauges have both "function" and "procedure" keywords.
6. Design Issues with Subprograms
	- Are procedures (no return value) and functions (yes) provided?
	- What are the semantics of parameter parsing?
	- What kinds of parameters are available?
	- Are types checked when actual parameters are parsed to the formal names?
	- Are there any restrictions on return types of functions?
	- Are return types checked when a function does a return?
	- How are local variables allocated in memory and when?
	- Does such allocation permit recursion? Restrictions?
	- Can subprogram names appear in a parameter list?
		- With what semantics/restrictions?
		- How is type checking done?
	- Does the signature of a subprogram constitute a type?
		- Can there be procedure variables of this type?
	- Can a procedure appear in its own parameter list?
	- Can a procedure name be overloaded with other syntax?
		- Say, as a replacement method?
	- Are subprograms separately compiled?
	- Is there a provision for forward definition of the header...
		- to accommodate one-pass compilers?
		- to allow mutual recursion?
	- Is there provision for providing a header for a subprogram in some pre-compiled library compiled from code in another language?
	- Is there provision for defining a header for a subroutine in the operating system
		- i.e. is there an interface to an API?
	- Are generic subprograms possible?
	- How are subprograms implemented?
		- Are they really just names for pointers?
	- Can subprograms overload operators such as +?
- When a (possibly recursive) instance of a subprogram is called (invoked)...
	- actual and formal parameters are matched
	- a chunk of memory is set aside for
		- return address
		- parameters
		- local variables
		- return value
	- the subprogram is given a pointer to the a.r. to access its contents
		- See next set for how this works conceptually.


**23. _Composition: Subprograms_**

**[3]** a. Compare the set of control structures in Ada with those in C# and say which are better and why?
- The set of control structures in Ada and C# are actually very similar in terms of functionality. Both languages have the standard if, case/switch, for, while, and exception handling statements. One major disadvantage to using Ada is the loss of *continue*, which is used to skip an iteration in a loop. Additionally, C# has more support for variations of standard loops, such as *do/while* or *foreach*, which Ada has not. This would lead me to say that Ada has worse control structures. One possible benefit to using Ada, is that in some cases it is far more readable, as much of the code is written in words rather than symbols.
https://learn.adacore.com/courses/Ada_For_The_CPP_Java_Developer/chapters/04_Statements_Declarations_and_Control_Structures.
https://www.geeksforgeeks.org/c-sharp-decision-making-else-else-ladder-nested-switch-nested-switch/

**[3]** b. What are the pros and cons for Python's use of indentation to denote compound statements in control statements? 
- There are many pros and cons of this method. One of the largest pros is that this can enforce readability, making the language easier to understand. However, this method of typing is unfamiliar to most other languages, which can lead to confusion from other programmers. When transferring a block of Python code between editors, sometimes the whitespace can be also removed, which leads to a painstaking process of re-indentation (avoided in languages which use {} to group blocks (C++)).

**[3]** c. Speculate on the reasons control can be transferred into a C loop statement
- It should certainly be possible to transfer control into C loop statements. This allows for iteration, and significant simplification of code. For instance, if I wanted to print out a line 10 times, I could use a *for* loop which iterates 10 times rather than using *printf("...")* 10 times. Some loops are controlled the "entry" path, such as *for* and *while*, which allows iteration based on a condition at the start of a code block. Others, such as the *do-while* loop are "exit" controlled, which evaluates if the loop should continue at the end of a block of code. This variability of where control is dealt allows for much more nuanced and effective programs to be written.
https://www.geeksforgeeks.org/c-loops/