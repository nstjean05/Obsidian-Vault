## 22.1 - Introduction
- Chapter focus on functionality of processors, memories, I/O devices, etc.
- Introduction of transistors and their use in logic gates.
- Explains how a clock can allow a basic circuit to combine and perform a sequence.
## 22.2 - The History of Digital Technologies
- Transistors were invented in 1947, and changed computing for several reasons.
	- Don't require filament
	- Low power consumption
	- Low heat production
	- Don't burn out
	- Low cost of production
- Modern computers built from electronic circuits using transistors.
## 22.3 - Voltage and Current
- **Voltage (V)**: Potential energy difference between two points
- **Current (Amp)**: Flow of electrons along a path (e.g. a wire)
- Using water as an example, voltage would correspond with its pressure, and current to the amount of water flowing through a pipe at a given time.
- If resistance remains constant, more current will lead to more voltage (Ohm's Law)
- A **Voltmeter** uses two probes to measure voltage.
	- To simplify measurement, the black probe is determined to be zero, and express the voltage of the second (red) point relative to zero.
	- The *zero* point is often referred to as the ***ground***.
- In computer science, we generally only need to know how electrical flow can be controlled and used to represent digital values.
## 22.4 - Transistors
- Transistors are the lowest level method of controlling electrical current in digital systems.
- **MOSFET** (Metal Oxide Semiconductor Field Effect Transistor)
	- A type of transistor used in digital circuits formed on crystalline silicon.
- They are used as an electrically-operated on/off switch.
	- Open or close based on the applied voltage.
- Each transistor has three terminals:
	- **Source/Drain**: Channel between these points on which resistance is controlled.
	- **Gate**: Controls resistance/flow through the transistor.
- There are two types of MOSFET transistors:
![[Pasted image 20250908143138.png]]
- The first flows when the gate is positive, and the second when it is negative.
	- When the voltage on the gate exceeds/it below a certain threshold, a current flows through the source/drain, and stops flowing when that threshold is no longer met.
- These two forms of transistor are known as **complementary**.
- 









## 22.7 - 