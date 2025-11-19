## 8.1 - Introduction
- Examination of memory addresses and byte addressing.
- Fetch-store paradigm
## 8.2 - Characteristics of Computer Memory
- Random access memory (RAM) is the primary memory for most computers.
	- Contains locations, each storing instructions or data
- Most RAM is *volatile*, meaning it is erased if power is cut.
## 8.3 - Static and Dynamic RAM Technologies
- *Static RAM* (SRAM)
	- Once a value is placed in memory, it stays until powered off.
	- Circuit for a bit has two inputs (input value, remember) and one output value.
	- To change the value, set the remember value to 1, and set the input.
	- To erase the value, simply turn remember off.
	- SRAM, although fast, consumes a lot of power to constantly supply each bit.
- *Dynamic RAM* (DRAM)
	- This circuit is structured the same, except it quickly loses its charge (sometimes in less than a second).
	- It needs an additional input, called a refresh, which re-writes the value back to the circuit.
		- The refresh circuit is more complex than this, but this is basically how it works.
	- Even though it is more expensive to add the refresh, DRAM saves so much energy that it is usually chosen over SRAM.
## 8.4 - Memory Performance and Higher Data Rate Technologies
- Vendors sell variants of DRAM with specific performance metrics.
- Clocks are used to control when read/write operations begin.
	- If the separate memory and processor clocks disagree, an extra clock cycle is taken to sync them.
- Most computers no use a **synchronous** clock system, combining the memory/processor onto one clock.
- Higher speeds can be gained by running the clock 2x or 3x the processor's top speed, so that it accesses memory faster.
- There are a large range of decisions to be made in RAM tech.
	- This has evolved many technologies, such as:
		- DDR-DRAM - Double Data Rate Dynamic RAM
		- DDR-SRAM - Double Data Rate Static RAM
		- FCRAM - Fast Cycle RAM
		- FPM-DRAM
		- QDR-SRAM
		- etc.
## 8.5 - Memory Addresses for an Array of Bytes
- Instructions cannot reference individual bits in memory.
	- Memory appears to be an array of bytes.
	- The array has an address starting at 0.
- Multi-byte objects (like an int) the operand specifies the address of the lowest byte.
	- Ex. A four-byte integer will occupy contiguous addresses
		- A, A+1, A+2, A+3
	- Instructions referencing that address will just use address A.
- Unsigned values *k* bits long can represent values from *0* to *2$^k$-1*.