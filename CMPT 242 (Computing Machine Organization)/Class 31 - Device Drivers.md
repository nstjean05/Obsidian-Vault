## Device Drivers
- ⁠Low-level interfaces between applications and devices
- Understand the CSRs (control and status requests) info from OS
	- Present a programming interface per OS specifications
	- There may in some cases (book says ‘are’) be part of OS (if generic) but usually they are plug-ins for specific devices
- Usually the data is to achieve device independence for applications
- They don’t need to know anything about devices - just talk to OS —> driver
- ⁠⁠i.e. We achieve device independence by:
	- Hiding details
	- Encapsulating handling code
## Consist Of
- **Lowest Level**
	- Interrupt handling codes
- **Upper Level**
	- API to request/handle I/O operations
- Shared variables (scratch RAM)
	- Registers
	- Flags
- Cache (speeds differ)
#### Device Types
- **Character Oriented**
	- Transfer 1 character/byte at a time
		- e.g. keyboard - one interrupt/character or byte
		- Some have line buffers
- **Block Oriented**
	- Transfer a block of B characters/bytes at a time.
		- Disk sector, network packet, data and error detection/prevention