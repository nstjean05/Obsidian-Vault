# 3.1 Introduction and Transport-Layer Services
- Transport services and protocols provide logical communication between application processes running on different hosts
- Transport protocol actions in end systems
	- Sender: breaks application messages into segments
#### Transport vs. Network Services and Protocols
- **Network**: Logical communication between hosts
- **Transport**: Logical communication between processes
	- Relies on, enhances, network layer services
#### Transport Layer Actions
- Sender...
	- Is passed an application-layer message
	- Determines segment header fields values
	- Creates Segment
	- Passes segment to IP
- Receiver...
	- Receives segment from IP
	- Checks header values
	- Extract application layer message
	- Demultiplexes message up to application layer socket
#### TCP and UDP Protocols
- **TCP** - Transmission Control Protocol
	- Reliable, in-order delivery
	- Congestion control
	- Flow control
	- Connection Setup
- **UDP** - User Diagram Protocol
	- Unreliable, unordered
	- No-frills extension of best effort IP
- Services not available:
	- No service has delay guarantees
	- No bandwidth guarantees
# 3.2 Multiplexing and Demultiplexing
- **Demultiplexing**: The process by which payloads are directed to the appropriate application or protocol running in a host
- **Multiplexing:** TCP funnels messages down into IP
#### Example
- Demultiplexing from server to client, so it can be displayed on browser
	- Demultiplexing splits something into small parts which are passed to their respective destinations
- On highway ramps, cars are multiplexed onto the highway when they merge in
	- Cars demultiplexed when split off into exits
- Multiplexing at sender
	- Handles data from multiple sockets, adding transport header
		- Header used for later demultiplexing
- Demultiplexing at receiver
	- Use header info to deliver received segments to correct sockets
#### Demultiplexing
- Host receives IP datagrams
	- Each datagram has source IP address, destination IP address
	- Each datagram carries one transport layer segment
	- Each segment has source, destination, port number
- Host uses *IP address and port numbers* to direct segment to appropriate socket
![218](Pasted%20image%2020261027152043.png)
#### UDP Connectionless Demultiplexing
- Recall: When creating a socket, one must specify the host-local port #
- When *creating* a datagram to send into UDP socket, must specify:
	- Destination IP address
	- Destination port #
- When *receiving* host receives UDP segment...
	- Checks destination port # in segment
	- Directs UDP segment to socket with that port #
- IP/UDP datagrams with same destination port #, but different source IP addresses and/or source port numbers will be directed to the same socket at receiving host
	- UDP demultiplexing only happens on the basis of the destination port number
![451](Pasted%20image%2020261027152601.png)
- On the other side...
	- P1 --> P4, Source: 6428, Dest: 5774
	- P4 --> P1, Source: 5774, Dest: 6428
#### TCP Connection-Oriented Demultiplexing
- TCP socket identified by 4-tuple
	1. Source IP
	2. Source port number
	3. Dest IP
	4. Dest port number
- Demux: (demultiplexing)
	- Receiver uses all four values to direct segment to appropriate socket
- Server may support many simultaneous TCP sockets
	- Each identified by its own 4-tuple
	- Each associated with a different connecting client process
![449](Pasted%20image%2020261027153113.png)
- Notice that the destination port number, in all diagrams, is 80
- In **UDP**, we would have demultiplexed solely on the basis of that destination port number
	- In **TCP**, because it is connection oriented, we demultiplex on the 4-tuple
	- Each of the 4-tuples of the 3 messages arriving are unique
# 3.3 Connectionless Transport: UDP
- 



































## Connectionless Transport: UDP
- **User Diagram Protocol - UDP**
- A no-frills internet transport protocol
- UDP segments may be lost or delivered out of order
	- "Best effort" service
- Connectionless
	- No handshaking between UDP, sender, receiver
- A UDP is useful for simple applications without a connection being established
	- Small header
	- No congestion control
- Used for
	- Streaming apps
	- DNS
	- SNMP
	- HTTP/3
- If reliable transfer is needed over UDP, then...
	- add reliability or congestion control at the application layer
#### UDP: Transport Layer Actions
- **Sender**
	- is passed an application layer message
	- determines UDP segment header fields values
	- creates UDP segment, and passes it to IP
- **Receiver**
	- receives segment from IP
	- Checks UDP checksum header vlaue
	- extracts application-layer message
	- demultiplexes message up to application via socket
- **UDP Segment Header**
- 32 bit segments, including:
	- segment 1: source port number & desk port number
	- segment 2: length & checksum
	- segment 3+: application data (payload)
- UDP ***checksum*** is meant to detect flipped bits in transmitted segment
	- Example: Transmitted first and second numbers are 5 and 6, making the sum 11
		- Receiver first and second numbers re 4 and 6, making the checksum 10 ≠ 11
		- An error will be detected
	- This is not a perfect system, as sometimes both numbers change, and the checksum is the same
## Principles of Reliable Data Transfer
- 