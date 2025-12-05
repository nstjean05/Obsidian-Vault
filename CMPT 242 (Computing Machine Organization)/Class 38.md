### Optimization
- Optimizations can be achieved by:
	- Replace some software functions with hardware
	- Produce better code for special cases (compile it!)
	- **Amdahl's Law**
		- Speedup is constrained by the amount of time the machine takes to execute the program
		- Rule of thumb: Only optimize what the program spends a lot of time on
	- BTW: Some I/O is the slowest, adding more/better/modern CPUs won't help
### Putting it all Together
- Architecture can be done on the level of the:
	- System - Macroscopic
	- Board - Mid level
	- Chip - Microscopic
### Bridges
- A bridge may be
	- On