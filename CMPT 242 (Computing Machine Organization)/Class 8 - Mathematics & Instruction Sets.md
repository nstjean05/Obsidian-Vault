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
- **Example:**
```
repeat
	check for data arrival
until check is valid

could be
	flag such as fuel low
	engine of fire
	out of candy bone
	device jammed
```
- The above are all imbedded systems
- Or in a CPU driven system:
	- Button pressed
	- key pressed
	- Mouse moved
	- Data on I/O bus
	- etc.
- Sometimes a processor waits in a "wait state" for a resource to become available or a co-processed task to complete.
#### Fetch-Loop
- A **fetch-loop** architecture implies that:
	- There is always something to do even if just wait.
	- A subroutine or program that gains control must eventually relinquish it to the controlling routine.
	- If no program is executing the processor loops in a wait state. (per the OS)
	- If there is a program running the processor loops in its own wait for an OS.
- JSR = Jump to Subroutine
- RTS = Return to sender
- After jumping to a subroutine, if nothing is found, the code may RTS.
#### The Startup Sequence
- Power on -  a reset zeroes out all gates (memory excluded)
- Processor jumps to a fixed address in ROM (expecting code there)
- ROM code there polls for an input device with storage looking for a device containing an OS, reads a specific track/sector into RAM.
- ROM transfers control to that code.
- This code loads the rest of the OS to RAM and jumps to it.
## Processor Tradeoffs
- Speed vs. complexity of the instruction set
- Complexity vs. heat production/power consumption vs battery life
- Speed or complexity vs. cost
- Convenience vs. simplicity
- A laptop tends to be simpler, slower, and uses minimal power compared to, say, a tower computer.
#### Instructions
- Instructions imply certain preconditions.
	- Ex. no divide by zero errors.
- Have an opcode representation in binary determining what to execute
- In many cases, the opcodes have operands with them.

8. _Chapter 4 concluded Chapter 5 started Note that Chapter 3 has also been done in bits and pieces._

a. **# 3.1, 3.2, 3.4**

**3.1** Give a mathematical proof that a string of k bits can represent 2k possible values (hint: argue by induction on the number of bits).


**3.2** What is the hexadecimal notation for the following binary string?
1101 1110 1010 1101 1011 1110 1110 1111


**3.4** Write a function that prints 1s and 0s for the individual bits of an integer. Add a space between bytes.

