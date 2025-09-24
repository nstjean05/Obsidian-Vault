## How to Optimize CISC
- Construction Instruction Set Computer (CISCI) is a computer architecture for computing complex, multi-step constructions the perform multiple operations at once.
- A pipeline is a sequence of instructions from a program.
	- The instructions are ordered one after another.
	- Occasionally it may be possible to complete instructions independent of one another, in which can you may form an additional pipeline.
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

| Clocktick | Stage 1      | Stage 2 | Stage 3 | Stage 4 | Stage 5 | Stage 6 |
| --------- | ------------ | ------- | ------- | ------- | ------- | ------- |
| 1         | Instruction1 |         |         |         |         |         |
| 2         | I2           | I1      |         |         |         |         |
| 3         | I3           | I2      | I1      |         |         |         |
| 4         | I4           | I3      | I2      | I1      |         |         |
| 5         | I5           | I4      | I3      | I2      | I1      |         |
| 6         | I6           | I5      | I4      | I3      | I2      | I1      |
- But if one instruction decides it needs to branch to a different memory location, it will erase the instructions before it.
	- Ex. if in Clock-tick 5, instruction 3 branches off, it will create a sort of 'bubble', as it erases instructions before it (4 and 5).
	- This leads to inefficiency if there is a lot of branching.
- Sometimes an instruction requires a result from another process, and so must wait for it to finish.
	- I2 requires a result from I1, and must wait for I1 to finish.
- An instruction may need a resource being used by one ahead of it.
	- Storage, co-processor, I/O device.
- A prior instruction branches, invalidating everything behind the pipeline and causing new code to load in it.
	- For this case, if you have two pipelines, there are several workarounds.
	1. Load the main code sequence as above in one pipeline, and the code for a branch the other.
	2. Have results from one pipeline forwarded to the other one.
	3. Have one pipeline, have an algorithm to predict the most common/likely result of a boolean meditated branch.
- Task one may be taking a long time on stage 3, leading to task 2 and 3 spending extra time in stage 2 and 1.
## Operator Types
- Arithmetic
	- Integer - In integer ALU (Arithmetic Logic Unit)
	- Boolean - In integer ALU
	- Floating Point Unit - FPU
	- Both FPU and ALU are now in CPU.
- Data Fetch
	- Move
- Branches
- Processor Control
- SP - Stack Pointer
- PC - Program Counter (Instruction address)
- Here is a sequence for an instruction I
	0. PC holds ADR(I)           SP = 0
	1. Length of I + PC pushed to CPU stack        INC(SP)
	2. Length of I + PC pushed to CPU stack        INC(SP)
	3. Pull SP to PC then DEC(SP)
	4. Pull SP to PC then DEC(SP)
	5. Pull SP to PC then DEC(SP)
- Suppose there is a branch during steps 3-5.


TO be continued on Friday





2. **W** _MIPS, branching, Start Chapter 6_

a. Make a list of differences between CISC and RISC chips and evaluate these differences for tradeoffs

b. **# 5.4, 5.5, 5.6, 5.7**