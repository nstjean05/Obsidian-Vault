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
## Types
- Parallel
	- One data channel for each bit plus control lines, ground, power
	- Can be very fast but doesn't scale up for wide (64-bit) busses.
		- Centronics connectors were used, 25/50 pins
	- Series
		- Channels for send, receive, signalling (2-3), ground, power (6-9 connections)
		- Control signals
			- DTR (data-terminal ready)
			- RTS (ready to send)
			- CTS (clean to send)
			- CLK (clock)
		- The most modern systems my automatically assert DTR and don't bother with RTS but may use CTS on a different pin.
## Interfaces
- Earlier - S232 - Confusion over which was a "terminal" (req. custom cables)
- Later serial interfaces included Firewire (400/800/1600)
- ESATA (Usually an internal bus/drive, but external cables were made)
- USB A - 1, 2, 3, 3,1, 3.2
- USB B - Style for peripherals, 4 kinds
- Potential speeds go up with every iteration of cable
#### Bi-Directional and Transfer
- Very important for, say, networking, and cloud computing/storage
- Is achieved with one of two protocols:
	1. Full Duplex
		- Complete set of lines in both directions
		- Send/receive are simultaneous
	2. Half Duplex
		1. Share 1 set of lines


25. _I/O_

a. Pick a current commercial system and report on its cache (L1, L2, L3, none, or…)

**12.1, 12.2, 12.3, 12.4, 12.**