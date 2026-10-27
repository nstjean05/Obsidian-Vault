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
	- Ex. HTTP --> port 80
	- Mail server --> port 25
	- To send a HTTP message to a server, you need the IP and the port
#### Application Layer Protocol
- Define:
	- The type of message exchanged
	- Message syntax
	- Message semantics
		- meaning of fields
	- Rules for when and how processes send and respond to messages
- Open protocols
	- Defined in RFCs (request for comment), everyone has access to protocol def
	- Allows for interoperability
	- HTTP, SMTP
- Proprietary protols
	- Skype, zoom
#### Transport Service for Apps
- Data integrity
	- Some apps require 100% reliable data transfer
	- Others, like audio, can tolerate loss
- Timing
	- Some apps require low delay to be effective
	- Ex. games
- Throughput
	- Some apps require a minimum amount of throughput to be effective
	- Others make what they can of what they get
- Security
	- Encryption
![](z.%20Images/Pasted%20image%2020261026230112.png)
- TCP Service:
	- Reliable transport
	- Flow control
	- Congestion control
	- Congestion oriented
	- Doesn't provide timing, minimum throughput guarantee, security
- UDP Service:
	- Unreliable data transfer
	- Doesn't provide reliability, flow control, congestion control, timing, throughput guarantees, security, or complete connection setup
	- However, we can build these additional services on top of UDP custom
![](z.%20Images/Pasted%20image%2020261026230259.png)
#### Securing TCP
- Vanilla TCP/UDP
	- No encryption
	- Cleartext passwords sent into the socket, traversing the internet as such
- Transport Layer Security (TLS)
	- Provides encrypted TCP connections
	- Data integrity
	- Endpoint auth
# 2.2 Web and HTTP
- 