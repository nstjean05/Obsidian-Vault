#incomplete 
### ADTs in Libraries
##### Typical Rules (may vary)
- The order of imports to a program unit determines one or more orders of compilation for the library modules (when they need to be (re)compiled)
	- This order may be different for the definition/interface/header parts and implementation/code parts.
	- Circular imports may mean there is no correct order.
- If the module/package/code body itself has code, it is executed in the order or import- i.e. this produces a link dependency.
#### Ada
- Allowed the interface and implementation parts to be...
	- Compiled as a single unit (i.e.. in one file)
	- Separately by specifying *separate*
	- Individual procedures could be marked *separate* and separately compiled as sub-units of the main package.
### Possible Issues of Separate ADT Compilation
- With few exceptions modules are not themselves types.
- When modules export types, the type details should either be...
	- marked in the interface as private
	- hidden in the implementation
	- If they are pointers to a hidden type, each instance must be explicitly created/destroyed.
	- If modules are types, the name of the module and the name of the type it defines may be identical and should be able to import the module and simple declare variables of that type (R-10)
- Libraries are themselves static
	- An instance, say of a binary tree might have to be generated for each node type, either by...
		- Duplicating the code with some changes.
		- Using generics, if available.
- Modules that export transparent types cannot control all operations on that type.
- Ones that export a pointer have all the pointer issues.
- When one binary depends on one or more others, there may be actions of which the programmer is unaware.
#### Questions to Ask
- If you do write a module for trees, say, how do you compare various items you want to entree?
- What are the semantics of items in a module?
- What are the rules for type compatibility with module entities?
- Can modules be used to overload operators for ADTs?
- Can a user-definable set of (default) imports be specified for the linker to they need not be intentioned in every program?
### Concurrency
- We often want to run more than one process at a time. We say such processes are *concurrent*.
- This can happen on several levels.
	- Instructions within the CPU
	- Statement - executing 2 or more simultaneously
	- Unit - One or more subprograms at once
	- Program - this is an OS issue.
- If there are more processors available than processes needing to run, each could have its own processor.
- If there are fewer processors that processes, some form of scheduling needs to happen.
### Vocabulary
- A *task* or *process* is a program unit in concurrent execution (related but /= to subprogram)
	- These may be stated implicitly and NOT be call-return
- Tasks are disjoint if they neither communicate with each other or share data (this is rare)
- Cooperative tasks must be synchronized to share resources.
### Concurrency Architecture
- Multiple processes simultaneously 