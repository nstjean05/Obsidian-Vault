## 5.1 - Introduction
- Focus on the set of operations that a processor can perform.
- Discusses the form of operands instructions use.
## 5.2 - Mathematics, Convenience, and Cost
- Even though humans and computers can do multiplication using addition or division using subtraction, it is much more efficient to multiple or divide.
- Repeated addition/subtraction results in horrible performance.
- Computers/processors are built with additional operations to improve performance, although this takes up more space on the chip and consumes more power.
	- How many operations should we add to a chip to balance usability/efficiency?
## 5.3 Instruction Sets
- Two decisions in designing programmable processors:
	- **Instruction Set**: Set of operations provided by the processor.
	- **Instruction Representation**: Format for each instruction.
- Assume that on each iteration of the processor's fetch-execute cycle, it will fetch and execute 1 instruction.
- *Instruction representation* refers to the binary representation that hardware uses for instructions.
	- Defines the interface between software that generates instructions, placing them in memory and;
	- The hardware that that executes these instructions.
- The software must create an image in memory that uses exactly the same instruction format that the processor expects.
## 5.4 - Instruction Set Architecture
- 1950s - Vendors designed each processor individually, with its own design goals.
- 1960s - IBM decides to use the same instruction set, so that all of their computers were compatible with one another.
	- This was the advent of IBM's *System/360* design.
	- Became much easier to upgrade a customer's system once they outgrew it.
- Modern CPU vendors use this same approach.
	1. Define an Instruction Set Architecture
	2. Offer a series of processor chips
		- Each implement the same ISA
		- Differ in speed, consumption, size, etc.
## 5.5 - Opcodes, Operands, and Results
- **Opcode**
	- Specifies the exact operation to be performed.
	- A unique opcode is assigned to each operation by the architect.
	- Ex. int addition might be assigned the nibble opcode 0100.
- **Operands**
	- This term refers the a value needed to perform an operation.
	- The definition of an instruction set specifies the exact number of operands and possible values for each instruction.
- **Results**
	- Some architectures allow one or more of the operand fields to specify where the processor should place results of the instruction.
	- Some architectures the location of the result is automatically chosen.
## 5.6 - Typical Instruction Format
- Each instruction is represented by a binary string.
- Opcode values specify how many operands to follow, and many specify the operand size.
## 5.7 - General-Purpose Registers
- *General Purpose Registers*
	- Used for variables, as storing them in memory for the program is slow.
	- Each register is a fixed size.
		- Processor with 32-bit arithmetic ==> 32-bit wide register.
	- Values from memory are placed in the register, and then all values and results are kept in the register.
		- Code may need to save the results in memory for later computation.
	- An access always returns the last stored value in the register.
## 5.8 - Floating Point Registers and Register Identification
- Floating point arithmetic often use a separate set of registers.
- General-purpose registers are used for integer values.
- The opcode will specify which to send a value to.
## 5.9 - Programming with Registers
- Sometimes the the instruction will also specify the type of register to send the computed value to.
- Leaving values in a register temporarily will save time, rather than storing it in memory right away.
- A compiler or programmer must decide which values to keep in a register at any given time.
	- Sent to memory at a given time.
	- This is known at *register allocation*.
- **Extended values** arise when instructions yield large results, leading to multiple registers combining to hold the value.
## 5.10 - Register Banks
- Some architectures divide registers into multiple **banks**, and require operands to come from separate banks.
- Register banks allow hardware to operate faster.
	- Each bank has a separate physical access mechanism, and the two mechanisms can operate simultaneously.
	- Placing the operands in separate banks can speed up access if they are called at the same time.
-  





## 5.11 - Terminology: Complex and Reduced Instruction Sets






## 5.12 - RISC Design and the Execution Pipeline






## 5.13 - Pipelines and Instruction Stalls






## 5.14 - Other Causes of Pipeline Stalls






## 5.15 - Consequences for Programmers






## 5.16 - Programming, Stalls, and No-Op Instructions






## 5.17 - Forwarding






## 5.18 - Types of Operations






## 5.19 - Program Counter, Fetch-Execute, and Branching






## 5.20 - Condition Codes and Conditional Branching






## 5.21 - Subroutine and Function Calls






## 5.22 - Argument Passing and Return Values






## 5.23 - An Example Instruction Set






## 5.24 - The Principle of Minimalism






## 5.25 - The Principles of Elegance and Orthogonality






## 5.26 - Summary





