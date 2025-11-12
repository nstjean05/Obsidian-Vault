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
- 