### Computing System Structure
- Software
	- Boot Firmware
	- ROM
	- OS
	- Programs
		- Tools
		- Util
		- Apps
- Hardware
	- CPU
	- Memory
	- Drivers for peripherals
		- GPU
		- UI
		- MegaByte Sections
- Dependent Data Types
	- Boolean
	- Pointers
- Dependancies
	- Width of data path
		- 8-16-64-128
### Von Neumann Architecture
- Binary Representation
- Sequential Access/Operation
- Memory Storage
### Topics
- Computer Arithmetic
	- Variation on common notation
- Boolean Logic
	- Circuits
- Hardware Organization
- I/O
- Memory
- OS
- Communications
### Types of Hardware
- Embedded
	- Car Chips, Elevator Real Time Systems, etc.
- Desktop/Laptop
- Mini Computer (Legacy)
- Mainframe (Legacy)
- Supercomputer (Cluster-format)




1. **W** _Chapter_ **_1_** _(introduction) Chapter_ **_22.1-22.3_** _Basic Circuits (1)_

a. List four reasons for studying hardware/low level concepts
1. Understanding what the computer is doing at a low level can help us write programs that utilize hardware more efficiently.
2. Our code can be written much more simply.
3. Low-level bugs and issues can be understood more quickly and easily, leading to simpler and less painfully-found solutions.
4. It is inherently interesting to learn about hardware, and it can help us get more excited about computers and working with them!

b. What is von Neumann computer architecture (three characteristics)
- Von Neumann architecture forms a computer utilizing three main components:
1. Processor - Executes program instructions.
2. Memory - Stores data for CPU processing.
3. Input/Output Facilities - Allow for interaction with the computer.

c. A computing machine based on von Neumann architecture can modify memory, including, possibly, that where the program instructions are stored (self-modifying code). Discuss the wisdom of allowing this to take place. 
- This allows a great deal of flexibility in programming, as the computer's abilities can be changed by the user's creativity, using the computer. It can also lead to very, very efficient programs (when written well), as the code can change itself as it goes. This also allows for marginally smaller programs, which may be necessary if storage is a constraint.

d. Explain what happens when you connect resistors (i) in series (ii) in parallel
- Resistors in series allow for the circuit's current to flow through the resistors one after another. The resistance of each resistor adds up, equalling the total resistance in the circuit. However, if the resistors are in parallel, then the current is divided amongst the resistors. The total resistance, in this case, is the sum of the reciprocals of each resistors resistance.

e. You have a supply of 10kΩ 5% resistors. (i) how are they marked? (ii) From these, show how to construct a 40kΩ resistor and a 2.5kΩ resistor
i) Brown, Black, Orange, Gold
ii) To create a 40kΩ resistor, simply add four 10kΩ resistors in series.  A 2.5kΩ resistor can be created by putting the same four resistors in parallel.

Textbook Questions:
**22.1** Use the Web to find the number of transistors on a VLSI chip and the physical size of the chip. If the entire die was used, how large would an individual transistor be?
- In order for a chip to be categorized as a *Very large-scale integration* (VSLI), it must have at least 10,000 transistors. Generally, these chips are 1-5 cm$^2$. For example, the Intel Itanium 9300 (released 2010) had a die size of ~699 mm$^2$, containing 2.046B transistors. If each of these were scaled up to fill the die, they would each be 3.418 × 10⁻⁷ mm².

**22.2** Digital logic circuits used in smart phones and other battery-powered devices do not run on five volts. Look at the battery in your smart phone or search the Web to find out what voltage is being used.
- My current (and favourite phone so far) is an iPhone 13 mini, which has a maximum battery voltage of 4.47V, although its standard voltage is below 4.3V.

**22.3** Design a circuit that uses _nand_, _nor_ and _inverter_ gates to provide the _exclusive or_ function.
![[Pasted image 20250909211745.png]]

| A   | B   | NAND(A,B) | NOR(A,B) | OR(A,B) | INV(A) | INV(B) | XOR(A,B) |
| --- | --- | --------- | -------- | ------- | ------ | ------ | -------- |
| 0   | 0   | 1         | 1        | 0       | 1      | 1      | 0        |
| 0   | 1   | 1         | 0        | 1       | 1      | 0      | 1        |
| 1   | 0   | 1         | 0        | 1       | 0      | 1      | 1        |
| 1   | 1   | 0         | 0        | 1       | 0      | 0      | 0        |
Deji Battery. (2024, January 16). _Understanding iPhone battery voltage and its relationship with capacity_. Retrieved from [https://www.dejibattery.com/News/understanding-iphone-battery-voltage-and-its-relationship-with-capacity.html](https://www.dejibattery.com/News/understanding-iphone-battery-voltage-and-its-relationship-with-capacity.html)

Encyclopedia. (n.d.). _Resistor network_. In _Encyclopedia of Electrical and Electronics Engineering_. Retrieved from [https://encyclopedia.pub/entry/31778](https://encyclopedia.pub/entry/31778)

Kerbiquet, M. (2024, April 30). _The lost art of assembly programming: Self-modifying code_. Tibleiz. Retrieved from [https://tibleiz.net/blog/2024-04-30-self-modifying-code.html](https://tibleiz.net/blog/2024-04-30-self-modifying-code.html?utm_source=chatgpt.com)

Pressbooks BCcampus. (2016, August 22). _Resistors in series and parallel_. In _College Physics_. Retrieved from [https://pressbooks.bccampus.ca/collegephysics/chapter/resistors-in-series-and-parallel/](https://pressbooks.bccampus.ca/collegephysics/chapter/resistors-in-series-and-parallel/)

Crowe, John. (1998). _Resistor networks_. ScienceDirect. Retrieved from [https://www.sciencedirect.com/science/article/abs/pii/B9780340645703500137](https://www.sciencedirect.com/science/article/abs/pii/B9780340645703500137)