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
#### MMU Page Tables
- Indexes all pages
- Has priority info
- Records what pages are loaded
- Say whether the page has been written to since last loaded - if dirty then write before purging
- May be stored in MMU but more likely in RAM (main memory)
- Clever use of binary enumeration to load pages of size s$^k$ bytes or address on 2$^n$ boundaries saves time.
- Paging can be sped up further with a TLB (translation look-aside buffer) in the MMU or high-speed RAM
- This contains a copy of the most recent page reference vectors (addresses) copied from the index of the page table the previous time it was used
- When a page is needed:
	- Two searches happen simultaneously
		- One in the page index
		- One in the *TLB*
#### Programming Tricks for Speed Advantage
1. Learn whether the OS/compiler stores arrays in row-major or column-major order and code your loops over arrays to match.
	- Row major:
		- | Row | Row | Row | ...
	- Column major: 
		- | Column | Column | ...


 2. _13. Finish Virtual memory and further on the MMU (storage schemes)_

**_No handins, but read Chapter 8 again_**