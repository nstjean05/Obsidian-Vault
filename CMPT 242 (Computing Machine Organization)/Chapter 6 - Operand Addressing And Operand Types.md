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
- 