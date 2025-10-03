- Similarly to languages, good processor designs are orthogonal.
	- Features are always used the same way.
	- Not different even in different contexts.
- In **branching**, each operation sets a flag in the flag register.

| Flag | Register             |
| ---- | -------------------- |
| V    | Overflow             |
| Z    | Last Result 0        |
| N    | Last Result Negative |
| C    | Last Result Carry    |
- Typically, you will perform the operation, and then test for a flag/branch.
- How many operands per operation?
	- None (Location of result known)
		- Ex. Stack operations
	- One (results are accumulated on a specific register)
		- Ex. 6502 - LDA #$A0 (load 0xA0 into A)
- Operands may be:
	- Literal (signed/unsigned)
	- Constant
	- Register
	- Memory Location
- Indirect Access
	- The operand contains an address where the data is located
		- Ex. MOV R1 (R2) - at R2 there is an address M
			- Get value M from R2 and use as an address






12. **Chapter** _6: Branching, operands, addressing modes_

  **# 4.1, 4.4, 4.12**