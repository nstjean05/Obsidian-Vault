### Memory Organization
- May be arranged like memory-in banks, each with its own controller to acheive some parallelism
- It may (usually) be distributed across chips with groups of bytes going in parallel to different banks.
- These schemes are transparent.
	- Programmers and even the OS don't need to know this.
- For very fast lookup of blocks of content carry content, *Content Accessible Memory* (CAM) may be used.
- A program or OS can have addresses by a key piece of content and associated address.
	- Very fast and expensive.
- One use of this is routers, where data packets are organized by IP address
	- Routers designed for home use are often not very good at this kind of thing.
	- IP address -> Input/Output -> cached
	- The information may be damaged when there is data coming/going from different locations.
### Virtual and Logical Organization
- These are abstractions of physical memory to hid implementation details and to create a higher level interface to lower-level details.
	- Ex. A virtual byte addressing scheme to isolate logical access from physical memory.
	- Installed memory usually isn't at contiguous addresses.
- The MMU maps the different...
	- Stored blocks
	- Paged out virtual memory
- As if it were contiguous actual memory
![](z.%20Images/Pasted%20image%2020251024124914.png)
- The MMU maps the memory to a contiguous block
#### Goals Achieved
- Heterogenous real memory can be homogenized
- MMU can enforce data protection, jail programs
- User Protection
- Processor mode switching can be tied to the MMU so, say, supervisory mode has its own memory.
- Code segmentation (allows for unused code to be swapped out)




21.  _Start on Virtual Memory_

**Read Chapter 9**

a. What is memory interleaving, and why would one want it in a machine?

b. Some memory chips have nine bits of storage for the eight bits of data. What is the extra bit used for?

c. Explain odd and even parity.

d. Explain CAM (Content Addressable Memory) The notes were a little weak.