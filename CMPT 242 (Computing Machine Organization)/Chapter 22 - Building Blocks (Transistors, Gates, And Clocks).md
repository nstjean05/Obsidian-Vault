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
- One interesting note is that due to the way electronic circuits work, it takes fewer transistors to implement the inverse of logical *or* and *and*, so we use *nor*,  *nand*, or *XOR* functions.
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
	- These expressions can be automated using editing tools, which is highly efficient, and can minimize your expression.
- You can also build *truth tables* (TT) for circuits like the one above to understand outputs.
	- Since there are 3 inputs, there are 8 possible outputs, but only one of these outputs is equal to 1 (where *X, Y, Z = 1, 1, 0*).
	- You can create a TT by starting with all possible inputs, and then fill out each column in the table one at a time.
	- These can be used to validate boolean expressions.
## 22.9 - Digital Circuits for Binary Addition
- You can add two binary numbers using the same method as you would in elementary school of carrying the 1.
	- Below is an example of adding *20 + 29* in binary.
![[Pasted image 20250909122923.png]]
- A circuit to do this form of addition needs a module per column.
	- The module for low-order bits takes two inputs, and outputs a ***sum bit*** and a ***carry bit***.
	- This circuit is called a *half adder*.
	- It contains an *and* gate and an *exclusive or* gate.
	- Depicted below is a *full adder* circuit.
		- You can see the two half adder gates nested within it, comprised of the two pairs of *XOR* and *and* gates.
![[Pasted image 20250909123159.png]]
- **The Sum**
	- The first and second *XOR* gates determine that the *sum* is only 1 if an odd number of inputs are 1.
		- For the first addition, the carry-in would be 0.
- **The Carry Out**
	- The first *AND* gate checks if both bits are equal to 1.
	- A second *AND* gate checks if the carry in and bit 1 XOR bit 2 are 1.
		- An *OR* gate combines these two *AND* gates.
	- Effectively, these gates make sure that the carry-out is 1 only if at least two of the inputs are 1.
- Below is the truth table for a full adder.

| bit1 | bit2 | carry in | sum | carry out |
|------|------|----------|-----|-----------|
| 0    | 0    | 0        | 0   | 0         |
| 0    | 0    | 1        | 1   | 0         |
| 0    | 1    | 0        | 1   | 0         |
| 0    | 1    | 1        | 0   | 1         |
| 1    | 0    | 0        | 1   | 0         |
| 1    | 0    | 1        | 0   | 1         |
| 1    | 1    | 0        | 0   | 1         |
| 1    | 1    | 1        | 1   | 1         |

## 22.10 - Multiple Gates Per Integrated Circuit
- Many Transistor-Transistor-Logic (TTL) gates can be manufactured onto a single component.
- An example of TTL components are the 7400 family.
	- Half-inch rectangular chips with 14 copper wires (pins), which connect to a circuit.
	- Results in the *14-pin Dual In-Line Package* architecture.
	- Some chips in this family are more complex, using more pins.
- Below are three simple chips in this family.
![[Pasted image 20250909132335.png]]
- Pins #14 and #7 are important, as they supply power and ground the gates.
- These chips are useful on a breadboard, as they make the components much smaller.
## 22.12 - Circuits that Maintain State
- ***Sequential Circuits*** are ones which take current inputs as well as previous ones.
- A ***Latch*** is a basic kind of sequential circuit.
	- It contains an input, output, and *enable line*.
		- If the enable line = 1, then the latch makes its output = input.
		- If the enable line = 0, then the latch freezes its output value at whatever it was at that instant.
		- This is a sort of 'remembering' the input from the time it was set.
- Below is a 1-bit latch comprised of 4 nand gates.
![[Pasted image 20250909135148.png]]
## 22.14 - Using Latches to Create Memory
- *Registers* in processors serve as short-term memory.
	- They generally hold values used in computation (e.g. to be added).
	- Each register holds a number of bits, most computers have 32 or 64-bit registers.
	- These registers are formed by lining up 1-bit latches alongside one another.
- Below is a 4-bit register.
![[Pasted image 20250909135611.png]]
## 22.15 - Flip-Flops and Transition Diagrams
- The output of a *Flip-Flop* changes when the input transitions from a 1 to a 0.
	- In order to output a 1, the input must be 0.
- An ***SR Flip-Flop*** one of four types of flip-flops.
	- It has two inputs, set and reset.
	- There are two possible states: active high (1) or low (0).
		- Active high means the circuit is usually at level 0, and go to 1 when active.
		- Active low indicates the circuit is usually at 1, dropping to 0 on activation.
	- If the set is high (1), then Q is set to 1.
		- When this set changes to 0, output Q will not change (it is latched).
		- When the reset input is changed to high (1), then Q can be reset to 0 given that set is also 0.
		- If set and reset both go high at the same time, an invalid state is triggered.
	- An active-low flip flop works the inverse of this.
![[Pasted image 20250909145242.png]]
- We can use an input diagram to see how a flip-flop changes over time.
	- Notice that in this example (where there is no *reset* input option), the flip-flop is only triggered when the input rises.
		- The *out* changes each time the *in* goes from 0-1
![[Pasted image 20250909150546.png]]
## 22.16 - Binary Counters
- A set of flip-flops can be connected in series to form a binary ***counter***, which can accumulate a numeric total.
- Counters (like flip-flops) have a single input, however they have multiple outputs.
- The outputs count how many input pulses have been detected.
	- Gives a numerical total in binary.
	- For example, a counter with 3 outputs can count up to 7 in 3-bit binary (111).

| Input | Outputs | Decimal | Time Increases |
|-------|---------|---------|----------------|
| 0     | 0 0 0   | 0       | 0              |
| 1     | 0 0 1   | 1       | 1              |
| 1     | 0 1 0   | 2       | 2              |
| 1     | 0 1 1   | 3       | 3              |
| 1     | 1 0 0   | 4       | 4              |
| 1     | 1 0 1   | 5       | 5              |
| 1     | 1 1 0   | 6       | 6              |
| 1     | 1 1 1   | 7       | 7              |
