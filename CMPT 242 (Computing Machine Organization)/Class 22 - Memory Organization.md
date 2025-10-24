### Memory Organization
- May be arranged like memory-in banks, each with its own controller to acheive some parallelism
- It may (usually) be distributed across chips with groups of bytes going in parallel to different banks.
- These schemes are transparent.
	- Programmers and even the OS don't need to know this.
- For very fast lookup of blocks of content carry content, *Content Accessible Memory* (CAM) may be used.
- A program or OS can have addresses by a key piece of content and associated address.
	- Very fast and expensive.
- One use of this is routers, where data packets are organized by IP address (input, output)
	- Routers de