*Notes based on **Essentials of Computer Architecture** by Douglas Comer, 3rd e.d.*
## 1.1 - The Importance Of Architecture
- Programmable processors are operating in nearly every system with hardware.
- Understanding hardware helps us write more efficient programs.
- Additionally helps to develop a holistic view of the systems we are designing.
## 1.2 - Learning The Essentials
- The text focuses on the basics from the ground-up, so not much background knowledge is required.
## 1.3 - The Cycle Of New Hardware And New Software
- A single optimal design for computing equipment has not been made, so there is still a lot of new computer architectures developing.
- New hardware --> New possible use cases --> More demand for new hardware/software --> Cycle continues
## 1.4 - What We Will Cover
- Four main components for building software:
	- Processor
		- Concerns both computation and control
		- Pieces connect to form a CPU
	- Memory
		- Holds programs and data as computer runs
		- There are physical and virtual memory systems
		- Concerns memory caching
	- I/O Devices
		- Input and output from the computer
		- Mice, displays, storage devices, etc.
		- Processors use a *bus* to communicate with a device
		- Drivers operate device software
	- Storage
		- Mechanisms to provide long term data storage for files
		- Block-oriented interfaces transfer data over a bus directory to/from memory
- Additional advanced topics such as pipelining and parallelism will also be covered.
## 1.5 - What We Will Omit
- This text is breadth over depth, concepts over details.
- Technical details are often ommitted, especially regarding processors or memory systems.