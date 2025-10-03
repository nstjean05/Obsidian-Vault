## CPU Design Considerations
- Central vs. Distributed Processing
	- **Central** - CPU
	- **Distributed** - Other Controllers
- CPUs have been becoming more complex but they don't do everything.
- A system may have other controllers/processors
- Protection is employed to give some subsystems higher priority access to the CPU or just clock cycles than others.
	- Prevent them from interacting with each other, the OS, or the CPU.
	- Enforce resource allocation
- Parallelism in hardware
	- So some processes do execute simultaneously within a CPU
		- Gates are replicated for each bit of each register.
		- Dual FPU (floating point unit) and ALU (arithmetic logic unit) units per core
		- Replication of cores
	- Various modes of execution
		- Supervisory or executive mode
			- High Priority
		- Standard Mode
			- Lower Priority
|Stupervisory Mode |