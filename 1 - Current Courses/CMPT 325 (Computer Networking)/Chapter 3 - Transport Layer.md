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
- An internet host has datagrams
- The 






























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