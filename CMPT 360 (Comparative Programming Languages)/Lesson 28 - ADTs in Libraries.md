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
- Multiple processes simultaneously (all requiring more than one processor)
	- **Parent Child** (auxiliary):
		- One CPU for the program, others for I/O
		- Almost all modern computers do this
	- **True Peer Multiprocessing** (multiple CPU cores)
		- Same process on different data
		- SIMD - single instruction multiple data (a common vector architecture has a register to share results)
		- Multiple synchronized processes
- Time Sharing
	- Where there are fewer processors that processes
	- Also called logical concurrency or quasi-concurrency
	- Here, several processes compete for time on one or more processors
	- **Note** that given problem may be solved either way
	- A producer-consumer system (such as a print buffer)
		- Units producing data send to the buffer, which sends to units consuming data.
	- All units must cooperate to maintain the data buffer
		- No two may update the shared resource simultaneously
		- A producer informs the buffer it has data waiting and suspends itself on a producer queue
		- A consumer informs the buffer it can accept data and suspends itself on a consumer queue
		- If the buffer can accept data it does so from the next producer on the queue until either the buffer is full or no more data
		- If the buffer has data it ships it to the next consumer on the consumer queue until the buffer is empty or consumer not ready
	- In this model the buffer ADT serves as a *monitor* or scheduler that controls the process suite.
		- A monitor is a *parent* or controlling process that determines when any other process in the suite may run. Those others are all *children*.
	- At any given time a task in the suite may be:
		- New (created)
		- Ready (suspended on a queue)
		- Running
		- Blocked (Stopped)
			- In an unflinching state due to...
				- An interrupt from a higher priority process
				- lack of a necessary resource
		- Dead (terminated) and unable to run.
	- **Note** A cooperative system is live if all its ready or blocked processes can eventually run.
	- **However** suppose we have two processes P and Q, both of which need resources R and S.
		- P locks R and requests S while Q locks S and requests R
		- So, P suspends itself to wait for S to signal ready
		- Q suspends itself to wait for R to signal ready
		- If neither can release its locked resource to allow for the other to run, the system is not alive.
		- We say is is *deadlocked* or in *deadly embrace*
### Process Synchronization
#### Semaphores
- If:
	- P processes can run at once
	- R Processes are currently running
	- A = P - R process *slots* are available.
- Therefore, if a process asks to run and A > 0, it can run, but if A = 0 it must be suspended on a *wait queue*
- If a process suspends, a slot is released
- If a resource is competitive a *binary* or *locking semaphore* can be used to signal *available* or *unavailable*
- **Note** if semaphores are set up or used improperly data will likely be corrupted.
#### Monitors
- One process is the parent or monitor it starts all the other processes and controls access to the standard resource.
#### Coroutines
- These are quasi-concurrent or time-shared processses each identified with...
	- A task
	- A memory block
	- A subprogram
- Initially one is the parent and dispatches control to another. After that control passes