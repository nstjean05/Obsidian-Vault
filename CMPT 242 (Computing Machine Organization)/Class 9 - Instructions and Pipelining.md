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
	- 






**9. M** _Chapter 5 5.1 - 5.20 Instructions, pipelining, optimization, and the PC and SC_

a. # **3.3, 3.12**
