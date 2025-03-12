#incomplete
#### Pointer Types
- Also known as *access types* (Ada) or *reference types*
- These types are pointers to or logical addresses of an entity residing at that location. 
- They may be themselves types so that
	- `POINTER TO REAL` has its own type distinct from `POINTER TO CARDINAL`
	- Or all just of types `ADDRESS` (or compatible with it)
- They have values in an abstract range of memory location
	- These are only connected to and not identical with machine addresses.
- They have a specific value, `NIL`, `nul`, or some similar name that points nowhere.
- They reference a particular type of data at that address
	- Where an appropriate amount of memory for the data is reserved heap-dynamically.
- They are not themselves structured types because they only have one component themselves - a virtual address.
	- What they point to is not a component of themselves.
	- So if `myPoint` is a pointer or reference to memory `myPoint` is an address of a location, a reference `myPointA` or `*myPoint` or `myPoint.` is the actual data.
#### Design Issues for Pointers
- Is the data type checked on assignment
	- e.g. If `p` is a pointer to an integer can you do `*p = 2.5` (or `p^ := 2.5`)?
	- And if so, what happens? Compiler error?
- What is their scope and lifetime?
	- The same rules as any other variable, or...
- Are dangling references (pointers whose memory is gone) and garbage (heap memory with no pointers) collected or allowed to accumulate?
- Are aliases (two pointers to the same memory) allowed?
- Are they used for other referencing?
	- Passing reference parameters objects?
	- Automatically or manually?
- How is the memory to which they point allocated? deallocated?
	- Auto or manual?
	- e.g. in C++ both are manual, but in Java they're automatic.
- Is nil, nul, NIL a reserved word or a standard identifier?
- Are pointers set to NUL on creation (i.e. automatic at declaration)
	- Failed allocation of memory
	- Deallocation
- What is their syntax and semantics





**17. _Dynamic data--heap storage, pointers, etc;_**

**[3]** a. What are the differences between C's malloc and free functions on the one hand and C++ new and delete on the other?
- The differences in malloc/new and free/delete seem not to affect the functionality, rather changing smaller details. For instance, *malloc* and *new* can each dynamically allocate memory, but new calls the constructor of a class although malloc does not. Furthermore, *free()* will free up memory but not call the class destructor, while *delete* will.
https://www.geeksforgeeks.org/new-vs-malloc-and-free-vs-delete-in-c/

**[3]** b. How do you declare dynamic types (with their pointers of course) in Modula-2, Ada, and C++
- Modula-2: 

https://www.modula2.org/tutor/chapter11.php

**[3]** c. Write a short discussion of what was lost and what was gained in the Java designers' decision not to have pointers as in C++ and other languages.

**[3]** d. What are the arguments for and against implicit heap storage recovery (such as in Java) and the explicit heap storage recovery used in C++. Consider real time systems.