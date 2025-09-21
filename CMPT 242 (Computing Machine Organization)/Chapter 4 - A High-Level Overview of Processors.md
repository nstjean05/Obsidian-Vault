## 4.1 - Introduction
- Overview of four main components of a computer.
- Explains the computer processor.
- Building blocks of a CPU.
## 4.2 - The Two Basic Architectural Approaches
- Two basic approaches emerged to computing early on.
	- Harvard Architecture
	- Von Neumann Architecture
## 4.3 - The Harvard and Von Neumann Architectures
- **Harvard Architecture**: A computer organization with four components:
	- Processor
	- Instruction Memory
	- Data Memory
	- I/O Facilities
![[Pasted image 20250916194734.png]]
- **Von Neumann Architecture**: A computer that uses a single memory to hold both programs and data.
![[Pasted image 20250916194821.png]]
- The primary advantage of *Harvard architecture* is that it can have the hardware of one memory unit optimized to store programs, and another optimized for data storage.
	- It is disadvantaged by its flexibility- you cannot use any instruction memory for data memory, or vice versa.
	- Harvard architecture is now almost only used in small embedded systems or otherwise special designs.
- Von Neumann offers complete flexibility, at the cost of only marginal efficiency loss.
	- This has led it to become the default architecture in computing.
- A computer that follows V-N architecture employs a *stored program* approach, since the program is stored in memory.
- These notes will assume V-N architecture unless otherwise noted.
## 4.4 - Definition of a Processor
- *Processor* is actually not a synonym for *Central Processing Unit (CPU)*.
- A processor actually has a much wider view in computer architecture.
	- Includes processors used in a wide variety of devices, such as automobiles or remote-control devices.
- **Processor**: A digital device that can perform a computation involving multiple steps.
## 4.5 - The Range of Processors
- There are four categories of processors according to how adaptable they are.
- **Fixed Logic Processor**
	- Least flexible, only performing a single task.
	- All functionality to perform the operation is built-in.
	- Functionality cannot be altered.
- **Selectable Logic Processor**
	- Often forms a subpart of a more powerful processor (like a CPU)
	- Contains hardware for more than one function.
	- Control lines to specify which function a given time.
- **Parameterized Logic Processor**
	- Only computes predetermined functions, but will accept a set of parameters to determine/variate that function.
	- Contains a function f(x) with variables p, q, and is able to change p and/or q each time the function runs.
- **Programmable Logic Processor**
	- Offers the most flexibility
	- Allows the sequence of steps to be changed each time the processor is invoked.
## 4.6 - Hierarchical Structure and Computational Engines
- A human cannot understand the complexity of a CPU, so we design/test it as separate separate units and then bring them together.
- Some of the subparts of a processor are so complex that they could be considered processors themselves.
- **Computational Engine**: Independent sub-piece of a large processor, which fulfills a specific role.
- For example, a CPU can contain a:
	- Trigonometry engine
	- Graphics engine
	- query engine
	- arithmetic engine
	- and more.
- **Graphics engines**









## 4.7 - Structure of a Conventional Processor











## 4.8 - Processor Categories and Roles


## 4.9 - Processor Technologies




## 4.10 - Stored Programs



## 4.11 - The Fetch-Execute Cycle



## 4.12 - Instructions in Memory



## 4.13 - Variable-length and Fixed-length Instructions



## 4.14 - Clock Rate and Instruction Rate



## 4.15 - Control: Getting Started and Stopping



## 4.16 - Starting the Fetch-Execute Cycle



## 4.17 Summary



