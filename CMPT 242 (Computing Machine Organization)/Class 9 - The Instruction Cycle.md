## The Instruction Cycle
- Loop
	- Look into memory indexed by *program counter* (PC)
	- Fetch instruction
	- Execute instruction
	- Increment PC
- End
- **Notes**
	1. The Amount of increment varies by instruction
	2. The number of clock cycles needed to execute an instruction varies by instruction
	3. The processor is always doing something even if waiting for some flag to be asserted.
