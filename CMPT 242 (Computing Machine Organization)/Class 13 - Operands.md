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
	- Various modes of execution:

| Supervisory or Executive mode                      | Standard Mode                                                 |
| -------------------------------------------------- | ------------------------------------------------------------- |
| High Priority                                      | Low Priority                                                  |
| Special Instructions                               | Somewhat limited standard instructions                        |
| Only usable on chip, or possibly by the OS         | Used by programs (compiled/assembled to)                      |
| All peripherals and memory are accessible to these | No Direct Usage - Access to memory is through the MMV (in OS) |
- **Examples** of some things that may be in a CPU

| Backwards Compatibility                               | Correct Mode                               |
| ----------------------------------------------------- | ------------------------------------------ |
| Ability to do 8 or 16-bit operations or run an old OS | Can only 32 or 64-bit operations on an OS. |
| **Exceptional Execution**                             | **Regional Execution Mode**                |
| Special handling behaviour                            |                                            |
| - On Chip, in the OS, and in your program             |                                            |
- How is the node changed











13. _Finish chapter 6:, operands, addressing modes_

a. Look up calculators with arithmetic logic, algebraic logic, and RPN logic. Consider an operation like 4 + 6*7 - 8 and determine how many key presses are required in each logic.

b. Describe at least 4 different modes of access (to data) that there are for instruction op codes?

c. **p123 #6.7, 6.11**