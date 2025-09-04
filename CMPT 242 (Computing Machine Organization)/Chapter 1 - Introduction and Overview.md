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
- Technical details are often omitted, especially regarding processors or memory systems.
## 1.6 - What We Will Emphasize
- Underlying computer hardware with most relevance to software engineering.
## 1.7 - Architecture, Design, and Implementation
- There are three primary levels of hardware specification:
	- Architecture
		- Overall organization of a system, forming its base.
		- Major modules of the software/components of the hardware.
		- Specifies functionality of each.
	- Design
		- Fill in details of modules.
			- Specifies the set of functions of a module and its algorithms.
		- Specifies how to achieve functionality for each component.
	- Implementation
		- Make choices for all the small things that the design omits
		- Choose a programming language
		- Exact components for the system
## 1.8 - Hardware Designs And Unexpected Constraints
- **Design Goals** and a **Set of Constraints** are required for design
- Other limits on functionality include power draw, system size, operational temperatures, electromagnetic radiation, etc.
- Very few hardware decisions can me made independently/without considering their impacts.
## 1.9 - Summary
- Course covers the essentials in computer architecture.