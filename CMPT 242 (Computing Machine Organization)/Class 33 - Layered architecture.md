## Layered Architecture
1. Applications
2. Run Time Library
3. O.S.
4. Device Drivers
5. Device
- Buffer size is generally at least 8k
## Parallelism
#### Version 1
- All computers are parallel processing at least on the microscopic level
	- This is the stuff that is transparent to users
- Multiple bits or bytes are processed simultaneously.
- Registers may function simultaneously
- Memory fetch/store
- Bus architecture for I/O
- Some use it macroscopically
	- Multiple Cores
	- Multiple CPUs
	- Multiple dissimilar CPUs (asymmetric parallelism)
		- a.k.a. Cluster Computing
#### Version 2
- Can be...
	- Fine grain - Operating on the individual instruction level
	- Coarse grain - Operating on the application level
#### Version 3
- May be...
	- Explicit - under program control
	- Implicit - automatic and invisible
#### Parallel Architecture Strategies
- **Note:** The term "parallel architecture" is used for scalable parallelism
	- i.e. A system to which we can add more CPU
- 