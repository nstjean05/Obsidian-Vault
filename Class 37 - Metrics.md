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