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
- This **CMOS** (Complementary Metal Oxide Semiconductor) chip technology is advantageous due to its exceptionally low power circuits.
## 22.5 - Logic Gates
- Because a transistor has only two possible states, we use boolean algebra to design circuits.
- **And**, **OR**, and **Not** are the three most basic boolean functions, shown below.
![[Pasted image 20250908143920.png]]
- A value of 1 represents true, while 0 is false.
- In a circuit, generally 1 = positive and 0 = no volts.
![[Pasted image 20250909104433.png]]
- **Case 1: Positive Voltage Input**
	- PMOS (top resistor) receives a high input, so it turns off. This means there is no connection between V$_d$$_d$ and the output.
	- NMOS (lower resistor) turns on because of the high input, connecting the circuit to the ground. This pulls the output down to ~0 volts.
- **Case 2: No Voltage Input**
	- PMOS turns on, as it is not receiving input. This connects V$_d$$_d$ to the output, leading to a large electrical output.
	- NMOS stays off as the voltage input isn't high enough, so the ground remains disconnected, allowing a high output.
- One interesting note is that due to the way electronic circuits work, it takes fewer transistors to implement the inverse of logical *or* and *and*, so we use *nor*,  *nand*, or *xor* functions.
	- This makes the inverse circuits cheaper to manufacture.
![[Pasted image 20250909105513.png]]
## 22.6 - Implementation of a Nand Gate
- Transistors in a circuit are called a *logic gate*.
	- Below is an example of a *nand* logic gate.
![[Pasted image 20250909105926.png]]
- If both inputs are equal to 1, then the output will connect to the ground.
	- Otherwise, at least one of the top two transistors will be on, connecting the positive voltage to the output.
- It is highly important that an output is never simultaneously connected to the source and drain simultaneously.
	- This would destroy the transistors.
- If there is a dot on two crossing lines, then there is a connection between them.
	- If there is no dot, or a break, then the lines don't connect.
## 22.7 - Symbols and Logic Gates
- There are many different symbols to quickly relate what a logic gate is doing.
	- This allows us not to think about transistors in every situation.
![[Pasted image 20250909115755.png]]
- Above are the most commonly used gates.
	- Two lines leading into a gate correlate with its inputs, while the line leading out is the output.
	- A circle ahead of the output line indicates the *not* version of the gate.
## 22.8 - Interconnecting Gates
- ***Transistor-Transistor-Logic*** (TTL) refers to the electronic parts that implement gates.
	- The output transistors in each gate are designed to connect directly to input transistors in other gates.
![[Pasted image 20250909120423.png]]
- In this example, the output can be said to be 'true' if the power button is pressed, and there is a Wi-Fi connection.
	- We use a *nand* gate connected to an *inverter* to return 1 (true) if both inputs are also true.
- These gates can also be expressed as a logical formula.
![[Pasted image 20250909120806.png]]
- Here is a process for deriving a boolean formula for the above:
	- The value @A corresponds with the function *not Y*
	- The value @B corresponds with the function *Z nor (not Y)*
	- The value @C corresponds with the function *X nand (Z nor (not Y))*
	- The output corresponds with *invert (X nand (Z nor (not Y)))*
- You can start your design process by coming up with a boolean expression that describes the behaviour you want in a circuit.
	- These expressios
## 22.10 - 
## 22.12 - 
## 22.14 - 
## 22.15 - 
## 22.16 - 