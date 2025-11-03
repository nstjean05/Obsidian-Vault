## I/O Devices and Busses
- Connect to the CPU like memory
	- Bus ==> Hardware
	- Selector/Manager ==> Hardware/OS
	- Some of these may be onboard the device.
- May have a dedicated processor
- Simplest paradigm:
	- Communication/Signal Channel/Data Bus
	- Tell device what to do (2-way comms.)
		- Send data
		- Get back status code
## Data Transfer
- Basic Idea
	- 2 types of device:
		- DTE - Data Terminal Equipment
		- DCE - Data Communications Equipment
	- CPU --> Interface Controller <--> ... Connecting coded 2-Way Comms ... <--> Interface Controller --> Device
	- 