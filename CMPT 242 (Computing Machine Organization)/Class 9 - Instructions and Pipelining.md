## Instruction Tradeoffs
- Make all instructions the same length
	- Simple, but wastes space
- Make instructions vary in length per use
	- Efficient memory but heavier load on the CPU.
- **Examples** of typical instructions:
	- Load a counter in register 6
	- Load memory into register 225
	- Move memory to a different memory
	- Move register " " register
	- Add register 1 to register 2 and put answer in register 3 or in memory
- **Registers** can be...
	- General purpose integer/word register
	- Specialized floating point, double, or quad wide.
	- If all registers are one single:
		- We may have a rule that a double loaded in register 4 --> 485
	- Allocated to the OS for specific purposes.
		- 1-10 for the results
		- 11-15 for counters
		- 16+ for scratch (temp. storage)
- In such a common strategy as 2-operand opcodes take/put in different banks
- **Assembler**
	- z <-- R6 + R5     (OK)
	- y <-- R7 + R2     (OK)
	- x <-- R0 + R1     (R0 and R1 are the same bank, not OK)
	- Go to [this link at Geeks for Geeks](https://www.geeksforgeeks.org/computer-science-fundamentals/what-is-register-memory/) to learn more.
![[Pasted image 20250922124050.png]]
## Instruction Sets May Be
- **Complex** (CISC)
	- Many instructions, each specific
		- Varying number of machine cycles
		- Some taking lots
	- Most processors from the big companies, especially before 2010
- **Reduced** (RISC)
	- Fewer instructions but more complex operations may take several
	- Fixed size
	- Are 1 clock-cycle each
	- Started with PowerPC chip (Apple/IBM/Motorola)




**9. M** _Chapter 5 5.1 - 5.20 Instructions, pipelining, optimization, and the PC and SC_

a. # **3.3, 3.12**
