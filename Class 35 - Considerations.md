## Pipelining Considerations
1. Hardware vs. Software
2. Small vs. Large Scale
3. Synchronous vs. Asynchronous
4. Buffered - Data moves in bursts
	- Unbuffered - Data goes in directly to the next stage
5. Streams that are chunked or un-chunked
	- If chunked, how big?
		- All the same size?
6. Automatic or manual data feed
	- Does the stage have to do a read/write cycle (normal)?
		- OR
	- Does an external mechanism control this?
7. Serial or Parallel data?
8. Homogenous or Heterogenous data
	- All the same kind?
9. 