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
- 