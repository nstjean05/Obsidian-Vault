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
- This allows a great deal of flexibility in programming, as the computer's abilities can be changed by the user's creativity, using the computer. 

d. Explain what happens when you connect resistors (i) in series (ii) in parallel

e. You have a supply of 10kΩ 5% resistors. (i) how are they marked? (ii) From these, show how to construct a 40kΩ resistor and a 2.5kΩ resistor

Textbook Questions:
**22.1** Use the Web to find the number of transistors on a VLSI chip and the physical size of the chip. If the entire die was used, how large would an individual transistor be?
- 

**22.2** Digital logic circuits used in smart phones and other battery-powered devices do not run on five volts. Look at the battery in your smart phone or search the Web to find out what voltage is being used.

**22.3** Design a circuit that uses _nand_, _nor_ and _inverter_ gates to provide the _exclusive or_ function.