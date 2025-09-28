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
- 






## 5.6 - Typical Instruction Format






## 5.7 - General-Purpose Registers






## 5.8 - Floating Point Registers and Register Identification






## 5.9 - Programming with Registers






## 5.10 - Register Banks






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





