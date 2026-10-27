# 2.1 Principles of the Application Layer
#### Some Network Apps
- Social media
- Web
- Text messaging
- Email
- Multi user games
- Streamed video
- P2P file sharing
- Search
- Voice over IP
- Remote login
#### Client-Server Paradigm
- **Server**
	- Always-on host
	- Permanent IP address
	- Often in data centres, for scaling
- **Clients**
	- Contact, communicate with server
	- May be intermittently connected
	- May have dynamic IP addresses
	- Do *not* communicate directly with one another
	- Ex. HTTP, IMAP, FTP
#### Peer-Peer Architecture
- *No* always-on server
- Arbitrary end systems directly communicate
- Peers request service from other peers, provide service in return to other peers
	- **Self Scalability:** New peers bring new service capacity, as well as new service demands
- Peers are intermittently connected and change their IP addresses
- More complex tracking of peers
#### Processes communicating
- Process - Program running within a host
	- The executing version of a program
- Within the same host, two processes communicate using inter-process communication
- Processes in different hosts communicate by exchanging messages
- **Client process** - Process that initiates comms
- **Server process**  - Process that waits to be contacted
#### Sockets
- Process sends and receives messages to and from sockets
- They act like doors
	- Sending process send message out the door
	- Sending process relies on transport infrastructure on the other side of the door to deliver the message
	- Two sockets involved in sender receiver comms; one for either side
#### Addressing Processes
- To receive messages, processes must have an identifier
- Host device has a unique 32-bit IP address4
- IP address isn't sufficient to identify the process running on the host
- **Identifier** includes IP and port numbers associated with processes
	- Ex. HTTP --> port