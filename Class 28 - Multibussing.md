## Multiple Busses
#### Different Types
- Busses may be of different or same types
- If of the same type, they need coordination
	- Main & Auxiliary portions
	- Peer to peer with an interconnecting bridge
		- Determines which bus gets the signals and data
		- We need even more signal lines
#### Switching Fabric
- Busses may need a switching fabric for interconnections
	- Simplest is allow only 2 busses to connect at any one time
	- More complex: allow any two non-overlapping pairs to connect.
- POTS - Plain Old Telephone System
- Crossbars of a mechanical type were the backbone of POTS
- In a computing system, a bus might have to switch up to 100 lines at once.
## I/O Part 2
- Here we are concerned with programmed devices.
- "Intelligent" rather than "dumb"
#### Synchronization
- CPU's can be up to 1000's of times as fast as a bus controller
- 