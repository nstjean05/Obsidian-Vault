## 6.1 - Introduction
- Focus on the operands used by instructions.
- Learn how human-preferred operands may not be optimal for computers
## 6.2 - Zero-, One-, Two-, And Three-Address Designs
- Instruction: Contains opcode, maybe followed by operands.
- The operation perform decides how many operands are necessary.
- The maximum number of operands is a debated topic.
	- Software eng - want as many as needed, like writing a code function
	- Hardware designers - Fixed length for faster execution
	- Parallel hardware seems good to fetch more data, but consumes much more energy.
	- Can instruction sets be designed without arbitrary operands?
## 6.3 - Zero Operands Per Instruction
- It is possible in some architectures for instructions to have no operands
	- This is known as **Stack Architecture**
	- The operands are kept implicitly on a stack in memory.
		- An internal register contains the address to the top of the stack, and the stack changes when an instruction is executed.
	- This stack uses standard push/pop operations.
	- It is disadvantaged, as it takes much long to get an operand from memory
- The instruction to add X + 7 would execute as such:
```
push X
push 7
add
pop X
```
## 6.4 - One Operand Per Instruction
- If there is a single operand per instruction, is a **Single Address** architecture.
- Again uses implicit operands per each instruction.
	- Stored in a special register called the *accumulator*
	- Each instruction contains 1 operand, and the processor uses the value in the accumulator as a second operand.
	- When the operation completes:
		- Processor returns result to the accumulator
	- Each instruction operates on the value in the accumulator.
		- Instruction to `add X` does `accumulator <-- accumulator + X`
## 6. 5 - Two Operands Per Instruction
- The *Two-Address Architecture* allows two operands per instruction.
- We can have operations like `add X Y`, which means `Y <-- Y + X`
- It can also move data very effectively, since it can specify a source and a destination.
	- `move Q R`
## 6. 6 - Three Operands Per Instruction
- This *Three-Address Architecture* enhances the data movement from two-address.
	- Now, we can add two values, and specify where they should be put.
	- `add X Y Z` would mean `Z <-- X + Y`
## 6. 7 - Operand Sources And Immediate Values
- There are many ways to use and obtain the operand data value.
	- **Operand used in operation**:
		- Signed/unsigned constant in instruction
		- Contents of a general purpose register
		- Contents of a memory location
	- **Operand used as result destination**:
		- A general purpose register
		- A contiguous pair of general purpose registers
		- A memory location
- **Immediate Values** (operand constants) are useful in many architectures
	- For instance, small constants that can be stored as an immediate value can be referenced frequently (incrementing a loop)
## 6. 8 - The Von Neumann Bottleneck
- Von Neumann Architecture: Programs stored in data and memory
- Memory access can become a bottleneck, as instructions are stored there.
	- Therefore there is one memory reference per instruction (minimum)
- If one or more operand is in memory, then there is a lot of time spent fetching.
- Efficiencies must be made by accessing operands in registers instead.
## 6. 9 - Implicit and Explicit Operand Encoding
#### Implicit Encoding
- The opcode specifies the types of operands
	- A processor using implicit encoding contains multiple opcodes for each operation.
- Below are addition instructions for a 2-address processor w/ implicit encoding.
	- Those that each combination of operations needs its own opcode.
	- Ex. *add immediate signed* has two operands:
		- First operand = register number
		- Second operand = Signed integer (immediate value)

| Opcode                 | Operands | Meaning                 |
| ---------------------- | -------- | ----------------------- |
| Add Register           | `R1 R2`  | `R1 <-- R1 + R2`        |
| Add immediate signed   | `R1 I`   | `R1 <-- R1 + I`         |
| Add immediate unsigned | `R1 UI`  | `R1 <-- R1 + UI`        |
| Add memory             | `R1 M`   | `R1 <-- R1 + memory[M]` |
#### Explicit Encoding
- Associates type information with each operand, so uses a much small set of opcodes than implicit encoding.
- An opcode (*and*) will have a multiple operands (operand 1, operand 2), each of which has its own type information and value (register, 1), (signed integer, 2)
## 6. 10 - Operands That Combine Multiple Values
- Unlike described in the prior section, some processors allow operands with more than one value.
	- It can be computed by extracting/combining values from multiple sources.
- **Register-Offset Mechanism:** Each operand consists of three subfields:
	- *Register-Offset*
	- *Register Number*
	- *Offset Value*
	- When an operand value is created, the contents of the offset field and the specified register are aded, and the result is used as the operand.
	- For example, below is an *add* instruction:
![](Pasted%20image%2020251111110129.png)
- It can be useful to allow an operand to specify a register plus an offset when dealing with a data aggregate (like a *struct* in C), since a pointer to it can be left in a register, and offsets used to reference individual items.
## 6. 11 - Tradeoffs in the Choice of Operands
- None of the described designs is definitively "the best", as there are many tradeoffs.
- **Ease of Programming**
	- Complex operands allow for easier programming.
	- Less steps to consider, easier to directly accomplish goals.
- **Fewer Instructions**
	- If one operand can do more things, then the number of instructions needed is less.
	- A 3-add





## 6. 12 - Direct and Indirect Operands in Memory






## 6. 13 - Illustration of Operand Addressing Modes






## 6. 14 - Summary
