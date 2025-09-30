## 1.1 - What Operating Systems Do
- A computer system can be divided into roughly 4 parts:
	- Hardware
	- OS
	- Application Programs
	- User
#### 1.1.1 User View
- The user has a number of I/O devices and applications to maximize the computer's usability.
	- Interaction goes from User --> Apps --> OS --> Hardware
- Many users now use touch screens or voice recognition as additional interaction.
#### 1.1.2 System View
- Operating systems are the computers **resource allocator**
- An OS is a **control program**
	- Manages the execution of user programs to prevent error.
#### 1.1.3 Defining OS
- An OS does not have any one definition, as there are so many applications.
- **Kernel** - The one part of an OS that is running at all times.
- **System Programs** - Associated with the OS but not part of the kernel.
- **Application Programs** - Not associated with the OS.
- **Middleware** - Set of software frameworks on mobile devices to provide services to application developers.
	- An expansion of sorts on the kernel.
## 1.2 - Computer-System Organization
- **Bus**: Connection between components (ex. CPU) and shared memory.
- **Device Driver**: A part of the OS that understands the device controller and provides the rest of the OS with a uniform interface to the device.
- All of these devices (CPU, USB controller for mouse/keyboard/printer, graphic adapter for monitor) are connected on the *system bus* to memory.
#### 1.2.1 Interrupts
- I/O operations begin as such:
	1. Device driver loads the appropriate registers in the device controller.
	2. Device controller examines the content of registers to determine an action to take.
		- Ex. Read character from keyboard.
	3. Controller begins to transfer data from device to local buffer.
	4. After data transfer completes, the device's controller tells its driver that the operation is finished.
	5. Device driver gives control to other parts of the OS
	6. For further operations, the device driver returns status information.
		- Ex. "Write completed successfully"
- **Interrupt**: How the controller informs the device driver that its operation is done.
	- Hardware may trigger an interrupt bus at any time by sending a signal to the CPU
	- When interrupted, the CPU stops what it's doing and transfers execution to a fixed location, containing the starting address where the service routing for the interrupt is located.
	- Below is an image of interrupt timeline for a single program completing output.
![](Pasted%20image%2020250930125116.png)
- **Interrupt Vector**: An array of addresses holding the interrupt service routines.
- **Interrupt-Request Line**: A wire in the CPU which it senses after executing each instruction.
- **Interrupt-Handler Routine**: When a controller is detected via signal on the line, the CPU reads the interrupt number as an index into the interrupt vector.
	- Execution begins at that address.
- Device controller ***raises*** an interrupt by asserting a signal on the line.
- CPU ***catches*** the interrupt, ***dispatching*** it to the handler.
- Interrupt handler ***clears*** the interrupt by servicing the device.
- Below is a diagram of the interrupt-driven I/O cycle
![](Pasted%20image%2020250930130618.png)
- Most CPUs have two interrupt request lines.
	1. **Non-maskable Interrupt:** Reserved for events like unrecoverable memory errors.
	2. **Maskable:** Can be turned off by the CPU before the execution of critical instruction sequences that mustn't be interrupted.
- **Interrupt Chaining**: There are too many devices (interrupt handlers) than addresses in the interrupt vector, so each element in the interrupt vector points to the head of a list of interrupt handles.
- **Interrupt Priority**: Levels allowing CPU to prioritize important interrupts.
#### 1.2.2 Storage Structure
- CPU loads instructions only from memory.
- **Random Access Memory** (RAM, Main Memory): Rewritable memory used to run programs.





## 1.3 - Computer-System Architecture














## 1.4 - Operating-System Operations





## 1.5 - Resource Management





## 1.6 - Security and Protection




## 1.7 - Virtualization
- NOT COVERED YET




## 1.8 - Distributed Systems
- NOT COVERED YET




## 1.9 - Kernel Data Structures




## 1.10 - Computing Environments




## 1.11 - Free and Open Source Operating
- NOT COVERED YET