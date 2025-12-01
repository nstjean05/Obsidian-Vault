# A Pipelining Example
- Switch/router data packets.
- Internet Sources --> Router --> Local Machines
- Routine:
	- Packet arrival kicks off the four stages;
	1. Verify data integrity
	2. Check for valid routing
		- No loops
	3. Determine correct route
	4. Transmit
- Suppose, for the sake of argument, that each of the four stages takes $\frac{1}{4}t$ (the time a single processor with no pipeline would take)
	- The first packet takes *t* time as it moves through the four stages
	- At this point the second packet has only one stage
		- It also takes $\frac{1}{4}t$ more time
	- The third packet, once packet #2 is done, also needs $\frac{1}{4}t$ more time
- **Note**
	- Speed is constrained by the slowest stage so partitioning into stages has to be done carefully and tends to be applications specific
		- Router pipeline != CPU pipeline
	- Note all tasks has 