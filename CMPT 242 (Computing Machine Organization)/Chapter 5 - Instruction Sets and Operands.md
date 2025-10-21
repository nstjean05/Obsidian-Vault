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
		- Every command that a given CPU can understand/execute.
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
![](z.%20Images/Pasted%20image%2020250929135919.png)
- Above is eight registers, in two banks.
- Sometimes a *register conflict* will occur if the two values being operated on are in the same register.
	- In this case, a compiler must insert an instruction to copy a value into another register bank.
## 5.11 - Terminology: Complex and Reduced Instruction Sets
- Instruction sets can be divided into two categories.
	- **CISC - Complex Instruction Set Computer**
		- Includes many instructions (hundreds), and each instruction can perform an arbitrarily complex function.
		- x86 instruction sets from Intel are CISC because it includes so many instructions, many which take a long time to execute.
	- **RISC - Reduced Instruction Set Computer**
		- A RISC instruction set is small compared to CISC.
		- RISC designs strive for the minimum set of instructions that is enough for all computations (e.g. totalling 32 instructions).
		- To achieve max speed, RISC constrains instructions to a fixed size.
		- RISC processors are designed to execute an instruction in one clock cycle.
- Modern computers with CISC instruction sets usually also contain a RISC design.
	- RISC engine performs the actual computation, decoding the CISC instructions.
	- CPUs have a lower engine built-in running *microcode* (learn more later)
## 5.12 - RISC Design and the Execution Pipeline
- RISC processors can complete one instruction on each clock cycle.
- **Fetch-Execute Cycle:**
	1. Fetch next instruction.
	2. Decode the operation specified by the opcode.
	3. Perform the operation.
	4. Perform memory read/write if needed.
	5. Store the result back to the registers.
- **Multistage Pipeline**: Parallel hardware units each perform one of the steps at a time.
	- Whenever the clock ticks, the instructions are passed down the line.
- Once the pipeline is full, then an instruction completes on each tick.
![](z.%20Images/Pasted%20image%2020251006103223.png)
## 5.13 - Pipelines and Instruction Stalls
- The instruction pipeline is *transparent* to programmers, as the instruction set doesn't explicitly reference a pipeline.
	- Hardware is constructed so the programs results are the same whether or not a pipeline is present.
- Programs think of instruction relative to another.
	- If instruction *K* is the focus, then behind it is *k-1*, and ahead is *k+1*.
- If an instruction doesn't complete and move on to the next stage in the pipeline, we say the pipeline has *stalled*
	- The instruction and all the ones behind it must wait until it continues.
	- The stall may be caused because the instruction is waiting for a previous one to, say, yield a value.
- Stalls have a negative effect on performance.
- When an instruction waits for one or more ticks for the one ahead of it, and then continues, we say that a *bubble* has formed in the pipeline.
## 5.14 - Other Causes of Pipeline Stalls
- There are number of reasons that pipelines may stall.
	- Accessing internal storage
	- Invoking a coprocessor
	- Branching to a new location
	- Calling a subroutine
- Some sophisticated processors contain extra hardware to avoid stalls.
	- Two copies of a pipeline
	- Shortcut hardware to pass a copy of a result back to a previous stage.
## 5.15 - Consequences for Programmers
- For maximum speed, programs on RISC should be written with accommodation to the instruction pipeline.
	- Separate references from when they are used in computation.
- Fortunately, compilers for high-level languages perform most optimizations automatically.
## 5.16 - Programming, Stalls, and No-Op Instructions
- Sometimes, rearranging to avoid stalls is not possible.
	- Documentation is important here so other users or programmers know about the stall.
- *No-op* instructions do nothing but occupy time, so that it doesn't look like a stall is occurring or a bubble is forming.
	- Use this in tandem with documentation.
## 5.17 - Forwarding
- **Forwarding*** is another technique to improve pipeline performance
	- Hardware can detect a dependency and pass the value forward.
- Ex. K computes the value C
	- K+1 needs the value C, so gets stuck.
	- When K finishes, the value C is forwarded.
## 5.18 - Types of Operations
- There are several categories of instructions:
	1. Integer arithmetic
	2. Floating point arithmetic
	3. Logical (boolean)
	4. Data access/transfer
	5. Conditional and unconditional branch
	6. Processor control
	7. Graphics
## 5.19 - Program Counter, Fetch-Execute, and Branching
- ***Instruction Pointer***: Hardware register to implement moving through instructions.
- Once an instruction is fetched, the program counter must update the address to and of the next instruction.
	- Allows the processor to automatically move on to the next instruction in memory when its task is complete.
- An *absolute branch* computes a memory address, and that address contains the location of the next instruction.
- A *relative branch instruction* doesn't specify an address, rather computing an increment for the program counter.
	- Ex. `br + 8` specifies branching to a location 8 bytes forward from the current one.
## 5.20 - Condition Codes and Conditional Branching
- *Conditional execution* is when a processor performs a different series of steps depending on its input value (pos/neg int).
- *Conditional branch* instructions allow the processor to decide amongst its options.
- *Condition codes* (held in registers) provide the basis for conditional branching.
	- Two values are produced after instruction computation:
		1. Result of computation
		2. Status
	- Operand in instruction says where to store result
- ALU sets a condition code to specify if the result is pos/neg/zero/overflowed.
	- A conditional branch then follows the operation.
## 5.21 - Subroutine and Function Calls
- Programs *call* subroutines, which *return* to the caller.
- Subroutines are also called subprograms, functions, and methods.
- Instruction implementing a subroutine must save the address of the caller before branching to the subroutine.
	- When it returns to the caller, subroutine must extract that address and branch to it.
- On the processor side, the address of the instruction is saved, but only after the instruction is used to invoke the subroutine.
	- This allows the processor to branch to the instruction after the call once control has returned to the caller.
- There are two general approaches to implementing subroutine calls:
	- Subroutine call instruction **pushes** the return address on the **stack**.
		- Used by earlier computers.
	- Subroutine call instruction **saves** the return address in a **register**.
		- Accessing a register takes shorter time than memory, so we gain efficiency this way.
		- The name `bl` (branch and link) is often used for the instruction that makes a subroutine call.
- Below outlines the fetch-execute cycle.
	- This is how the hardware computes the next step.
```
Assign the program counter an initial address, and repeat forever{
	Fetch: Access next step of program from the location given by program counter
	
	Set an internal register (A) to the address beyond the instruction just fetched.
	
	Execute: Perform the step just fetched
	
	Copy the contents of A to the program counter.
}
```
## 5.22 - Argument Passing and Return Values
- **Parameterized Subroutines**
	- When a function is called/method invoked, the calling code *passes* on a set of arguments to the subroutine.
- *Calling sequence* is the order of steps taken when calling a subroutine.
- There are a limited number of registers, so you must wisely choose what to use them for.
	- Arguments = Faster subroutine calls
	- Computation = Faster execution of instructions
- If a value in a register is needed later, it must be saved elsewhere before that register can be used.
- **ARM** compromises the tradeoff as such:
	- Registers 0-2 for the first few arguments.
	- Stack is used for any further arguments.
	- Other registers used for computation.
- This balances speed, flexibility, and efficiency.
## 5.23 - An Example Instruction Set
- The MIPS processor is a good example, as it is small and easy to understand, as well as includes a wide enough range of concepts.
- MIPS = Microprocessor without Interlocked Pipelined Stages
- A MIPS processor has 32 general-purpose registers.
- MIPS architecture defines a set of floating point instructions for single and double precision floating point values.
	- These are separate from the general registers.
	- Floating point registers operate as pairs to handle double precision values.
- Find a copy of the instruction set here: https://www.dsi.unive.it/~gasparetto/materials/MIPS_Instruction_Set.pdf
## 5.24 - The Principle of Minimalism
- The MIPS instruction set has two goals: speed and minimalism.
	- Designed to be fast, especially given pipelines.
	- Contains the fewest possible instructions for standard computation.
- Minimalism is important, as additional operations require more physical circuitry, which drain power passively.
- MIPS register 0 always contains the value 0; therefore any register can be tested if it contains 0 by comparison.
## 5.25 - The Principles of Elegance and Orthogonality
- An architect must consider elegance—how the instruction set will appear to programmers.
- Orthogonality states that we must minimize overlap between instructions.
	- An instruction set is *orthogonal* if each instruction performs a completely separate task.
	- This takes away the 





## 5.26 - Summary





