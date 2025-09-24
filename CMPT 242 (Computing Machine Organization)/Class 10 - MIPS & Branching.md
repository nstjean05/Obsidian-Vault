## How to Optimize CISC
- Construction
1. Do make every instruction the same length as in RISC
2. Take the cycle
	1. Fetch instruction
	2. Check code for # of operands
	3. Fetch operands
	4. Perform operations
	5. Store results
3. Pipeline it with stages for each instruction
	1. Clock Tick #...
		1. Fetch instruction 1
		2. Move instruction 1 to stage 2, fetch instruction 2
		3. etc.

| Clocktick | Stage 1      | Stage 2 | Stage 3 | Stage 4 | Stage 5 | Stage 6 |     |     |     |
| --------- | ------------ | ------- | ------- | ------- | ------- | ------- | --- | --- | --- |
| 1         | Instruction1 |         |         |         |         |         |     |     |     |
| 2         | I2           | I1      |         |         |         |         |     |     |     |
| 3         | I3           | I2      | I1      |         |         |         |     |     |     |
| 4         | I4           | I3      | I2      | I1      |         |         |     |     |     |
| 5         | I5           | I4      | I3      | I2      | I1      |         |     |     |     |
| 6         | I6           | I5      | I4      | I3      | I2      | I1      |     |     |     |
- But if one instruction decides it needs to branch to a different memory location, it will erase the instructions before it.
	- Ex. if in Clock-tick 5, instruction 3 branches off, it will create a sort of 'bubble', as it erases instructions before it (4 and 5).
	- This leads to inefficiency if there is a lot of branching.


5. **W** _MIPS, branching, Start Chapter 6_

a. Make a list of differences between CISC and RISC chips and evaluate these differences for tradeoffs

b. **# 5.4, 5.5, 5.6, 5.7**