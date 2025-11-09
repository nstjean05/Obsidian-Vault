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
	- It is disadvantaged, as it takes much long to get an operand from memory.
## 6.4 - One Operand Per Instruction
- If there is a single operand per instruction, is a **Single Address** architecture.
- Again uses implicit operands per each instruction.
	- Stored in a special register called the *accumulator*
	- Each instruction contains 1 operand, and the processor uses the value in the accumulator as a second operand.
	- When the operation completes:
		- Processor returns result to the accumulator
	- Each instruction operates on the value in the accumulator.




## 6. 5 - Two Operands Per Instruction






## 6. 6 - Three Operands Per Instruction






## 6. 7 - Operand Sources And Immediate Values






## 6. 8 - The Von Neumann Bottleneck






## 6. 9 - Implicit and Explicit Operand Encoding






## 6. 10 - Operands That Combine Multiple Values






## 6. 11 - Tradeoffs in the Choice of Operands






## 6. 12 - Direct and Indirect Operands in Memory






## 6. 13 - Illustration of Operand Addressing Modes






## 6. 14 - Summary
