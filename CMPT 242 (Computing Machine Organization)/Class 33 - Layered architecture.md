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
#### Flynn Classification for Macroscopic Parallelism
- **SISD** - Single instruction single data store
	- No Parallelism
- **SIMD** - Single instruction multiple data
	1. Vector Machines
		- Execute the same instruction on vectors - say multiple vector multiplications at once.
		- Matrix multiplication is a good example.
	2. Graphics Processors
		- May move whole screenfuls of data (or at least windows) at once - copying multiple bytes simultaneously.
- **MIMD** - Multiple Instruction Multiple Data
	- Processors perform multiple data operations simultaneously
		- **Symmetric Multiprocessing** (SMP)
			- True Multiprocessing
			- Multiple identical processors
			- In theory these are peers and independent.
		- **Asymmetric Multiprocessing** (AMP)
			- May be different
			- Two methods;
			- One runs a monitor or master processor, the rest are slaves reporting back to it.
			- **OR** - One starts up the others and passes control to them but each listens so the system can regain control.
- Specialized processors for a multiprocessing environment
	- Matl (not common today)
	- Graphics (usually the case - GPU)
	- I/O
	- Peripheral processor (I/O or other things)
- Performance Issues
	- Overhead needed for
		- Communication
		- Coordination (master/slave, cooperative)
		- Contention Resolution (scheduling resource use)