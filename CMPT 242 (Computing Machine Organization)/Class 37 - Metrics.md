# Metrics
1. Raw processor speed (GHz)
	- Says how fast the main clock ticks.
2. Average number of cycles per instruction overall.
	- Could be different if optimized for floating point.
	- This is ok if you are doing mostly integer arithmetic.
3. Since FP operations are usually the slowest, we can also measure speed in MegaFLOPS.
4. Because in many systems, different instructions take different units of time, we could compute a weighted average instruction time.
	- $T_a$$_v$$_g$ - After measuring the time/instruction in a suite
5. (Somewhat Obsolete)
	- Sieve of Eratosthenes
		- Went out of use, as compiler makers started inserting highly efficient algorithms that detected the sieve, and ran it really fast to trick the benchmark.
	- Whetstone
	- Dhrystone
	- These all have standard completion run times.
6. Problems with benchmarks:
	- Processor intensive so do not measure other things like I/O
	- Compilers can detect when one is running & cheat with optimized code.
	- Results may depend on the compiler and language
	- SPEC - Standard performance evaluation corporation
		- A series of specialized benchmarks to measure integer and FP speeds
		- Many vendors cite mark results.
	- Application suite bench marks
		- Common in trade publications, they run a collection of common apps to simulate what a user might do.
		- Tend to lean toward power users.
			- WP, DB, SS, Graphics, Browser, compiler framework, editor, etc.
		- They weight these and report results
	- Advantages: Try to be realistic
	- Disadvantages:
	- Over time the have to be changed - only valid for the current go.