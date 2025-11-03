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
- 