## Other Memory Management Aspects
- All run by the MMU
#### Base-Bond Registers
- Set in MMV by the OS to give each person code and data memory
- Allows for protection
	- priorities when released
	- against trespass by other programs
#### Code Segmentation
- Code is divided into blocks - not all may remain in memory
	- Could be parked as "purgeable" or "locked"
- Not used frequently today.
- **Problem**: Having different sized blocks can create memory problems
- **Solution**: All blocks are the same size (may waste memory)
	- This is called *demand paging*
- Needed code in MMV to detect page faults (page/block need but not loaded)
	- Code to prioritize pages
- 