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
- **Graphics engines** (aka graphics accelerators)
	- Used to drive the graphics display at a high speed.
- **Query engines** are used in database processors.
	- Examines a record and quickly determines if the query is satisfied.
- **Pattern Engines** are similar to query engines.
	- Examine a string of bits to determine if the string matches a specified pattern.
## 4.7 - Structure of a Conventional Processor
- Most processors do not include engines.
- A practical processor has 5 conceptual units:
	- **Controller**
		- Overall responsibility for program execution.
		- Walks through the program and coordinates actions of all other hardware units.
	- **Local Data Storage**
		- A processor must have at least some data to hold values.
		- Values often loaded onto *registers* before computation.
	- **Internal Interconnections**
		- Physical hardware for transferring values between units.
		- Also known as *data paths*.
	- **External Interfaces**
		- Communications between processor, external memory, and I/O.
![[Pasted image 20250920204415.png]]
## 4.8 - Processor Categories and Roles
- There are many examples of hardware devices using processors. Below are some examples.
- **Coprocessors**
	- Operates with and controlled by another processor.
	- Generally, the coprocessor is very specialized and very fast.
	- Ex. *Floating point accelerators* for the arithmetic operations.
	- When a floating point operation occurs, the CPU automatically passes the values on to the coprocessor.
	- Some architectures are not sure which operations are performed by CPU and which by a coprocessor.
		- We would say that operation of the coprocessor is **transparent** to the software.
- **Microcontrollers**
	- A programmable device dedicated to controlling a physical system.
	- Run things like car engines, automatic doors, etc.
	- Tests sensors, performs functions.
	- Generally don't do much computation.
- **Embedded Systems Processors**
	- Runs a sophisticated electronic device
		- Ex. wireless router, infotainment in a vehicle, etc.
	- More powerful than microcontrollers, often running protocol stacks for communications, but not functional like a CPU.
- **General-Purpose Processor**
	- These are what we're most familiar with, used in laptops or smartphones.
## 4.9 - Processor Technologies
- 1960s - Processors made by connecting individual transistors on a circuit board.
- 1970s - Large-scale integrated circuit technologies.
		- Allow for the least powerful processors (e.g. microcontrollers) to be created on an integrated circuit (IC).
- As IC technology improved and number of transistors on a chip increased, a chip can hold more powerful processors.
- Most powerful processors today are often a single IC.
## 4.10 - Stored Programs
- Processors perform computations with steps
	- Some processors have these steps built-in, but most don't
- Most processors use programming to provide the step sequence
- Conventional computers load the program into memory when an application is run.
	- This program can be changed on the next run.
- Microcontrollers use *Read Only Memory* (ROM), with programming that is locked-in the harware.
- Programmable if the processor is separate from its program.
## 4.11 - The Fetch-Execute Cycle
- Programmable processors must access and perform steps from a program.
	- This is the *fetch-execute* cycle.
- A processor has a pointer to an instruction, automatically moving the program into memory, performing each piece.
- This gives us many questions.
	- How does the processor know the next step in program?
	- How is an operation performed?
	- How are the instructions represented in memory?
	- etc.
## 4.12 - Instructions in Memory
- Each instruction occupies a set of sequential bytes in memory.
- The compiler (which generates the bits to be stored in an instruction) and the interpreter (which translates the instruction for the hardware) must agree on all details.
- Processors divide the bits of an instruction into *fields*
- *Opcode* (operation code) is the most important field in an instruction.
	- It specifies the operation to perform.
- Other fields specify the *operands* to use when the instruction is executed.
## 4.13 - Variable-length and Fixed-length Instructions
- *Variable-length instructions* allow for some instructions to take up more or less bytes.
- 














## 4.14 - Clock Rate and Instruction Rate















## 4.15 - Control: Getting Started and Stopping















## 4.16 - Starting the Fetch-Execute Cycle















## 4.17 Summary



