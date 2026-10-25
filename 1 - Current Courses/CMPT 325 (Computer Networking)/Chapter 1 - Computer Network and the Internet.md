#incomplete 
# Videos
- 1.1 - https://www.youtube.com/watch?v=74sEFYBBRAY
	- Intro
- 1.2 - https://www.youtube.com/watch?v=k8NmM-hImBU
	- Network Edge
# What is the internet?
- The internet is made of many connected computing devices
	- Hosts = endpoint systems
	- Runs network apps at the internet's 'edge'
- **Packet Switches**: Forwarding packets
	- Done via routers and switches
- **Communication Links**
	- Fiber, copper, radio, satellite
	- *Bandwidth* describes the transmission rate
- **Networks**
	- Collection of devices, routers, and links, which is managed by some organization.
- **Internet**: A network of networks
#### Nuts and Bolts View
- **Protocols** control sending and receiving of messages
	- They are everywhere, and describe the standard way of doing things
- Standards:
	- RFC: Request for comments
	- IETF: Internet engineering task force
#### Services View
- As a service:
	- Major infrastructure
	- providing services to apps for web streaming, email, games, e-commerce, etc.
- Provides a programming interface for distributed apps
	- Hooks allowing send and receiving
#### Internet Protocols
- A protocol is a method of communicating
- Rules for messages sent and actions taken
- Human protocols
	- What's the time?
	- Do you have any questions?
- Network protocols
	- Devices (computers)
- Connection request phase, followed by a connection response phase
	- Ex. Request for time: Hi --> Hi --> Got the time? --> 2:00 --> Thanks
	- Ex. TCP connection request --> TCP connection response --> File transfer
- Protocols define the format and order among network entities.
## Network Edge
- Interconnected routers - inter net
- There are several kinds of access networks
	- Residential
	- Institutional
	- Mobile
- What is the transmission rate, and how much is it shared between users?
- *Connection Oriented*
	- Prep data transfer ahead of time
	- Establish a connection in the two communication hosts
	- Has reliability and flow/congestion control
	- Internet: TCP (Transmission Control Protocol)
- *Connectionless*
	- No connection setup
	- Faster, less overheadµ
	- Low reliability, no flow control
	- Internet: UDP (User Datagram Protocol)
- **Access Networks**
	- Wired, wireless communication links
- **Network Core**
	- Interconnected routers
	- Network of networks
#### Residential Access Network 
1. Cable Based
	- Frequency Division Multiplexing: Different channels transmitted in different frequency bands
	- HFC: Hybrid fibre coax - high downstream transmission (1.2 Gbps), low upstream (100 Mbps) (1/10th)
		- If your neighbour is using a lot of it, you can feel your bitrate drop.
	- Network of cable, fibre attaches homes to ISP router
	- Sent at multiple frequencies which don't interfere with one another.
2. Digital Subscriber Line (DSL)
	- Used existing telephone line to central office DSLAM
		- Data over DSL phone line goes to internet
		- Voice over DSL phone line goes to telephone net
	- 24Mbps down, 3.5 Mbps upstream
#### Home Access Networks
1. Wireless Access Networks
	- WLAN: Wireless Local Area Network
		- 100ft range
		- 11/54/450 Mbps transmission
	- Wide-area cellular access network
		- Provided by mobile network operator
		- 10s of kms
		- 4G/5G cellular networks
2. Enterprise Networks
	- Companies, universities, etc.
	- Mix of wired/wireless, switches/routers
	- Eth: 100Mbps, 1Gbps, 10Gbps
	- WiFi: 11, 54, 450 Mbps
3. Data Center Networks
	- High-bandwidth links (10s-100s Gbps) connect 100s of servers together
#### Sending and Receiving Packets
- **Hosts**
	- Take app message
	- Breaks into smaller chunks (packets)
	- Packets of data
		- *L* bits long
		- *R* transmission rate
		- Link capacity = bandwidth
- **Physical Links**
	- **Bit**: Propogates between transmitter/receiver pairs
	- **Physical Link:** What lies between the transmitter and receiver
	- **Guided Media:** Signals propagate in solid media (e.g. copper, fiber, coax, etc.)
	- **Unguided Media:** Signals propagate freely (e.g. radio)
- **Coaxial Cable**
	- Two concentric copper conductors
	- Bidirectional
	- Broadband
		- Multiple freq channels on cable
		- 100s Mbps per channel
- **Fiber Optic Cable**
	- Glass fiber carrying light pulses, each pulse a bit
	- High-speed operation, 10s-100s Gbps
	- Low error rate
		- Far-spaced repeaters
		- Immune to electromagnetic noise
- **Wireless Radio**
	- Signal carried in various bands in electromag spectrum
	- No physical wire
	- Broadcast
	- Propogration environment effects
		- Reflection
		- Obstruction by objects
		- Interference/noise
- **Radio Link Types**
	1. Wireless LAN (WiFi)
		1. 10-100s Mbps, 10s meters range
	2. Wide Area (4G/5G)
		1. 100s Mbps, over 10km
	3. Bluetooth (replaces cables)
		1. Short distances & limited rates
	4. Terrestrial microwave
		1. Point to point, 45Mbps
	5. Satellite
		1. Up to 100Mbps downlink
		2. 270 ms end-end delay
# Network Core
- Interconnected routers
	- A network of networks
- **Packet switching:** Hosts break application-layer messages into packets
	- Forward packets from one router to the next, across links on the path
	- Each packet is transmitted at full capacity
- Fundamental Q: How is data transferred on the net?
	- **Packet Switching:** Sent through the net in discrete chunks
	- **Circuit Switching:** Dedicated circuit for each call
#### Packet Switching
- Transmission delay: Takes L/R seconds to transmit L-bit packets into link at R bps
- Store and forward: entire packet must arrive at router before it can be transmitted on
- End-end Delay: 2L/R, assuming zero propagation delay
- Forwarding is a local action - moving arriving packets from routers input to output links
- Routing is a global action - determining source destination paths that packets traverse
	- Uses routing algos (Dijkstra)
- Queuing occurs when work arrives faster than it cna be serviced
- Packet queuing and loss
	- If arrival rate in bops

# Performance


# Security


# Protocol Layers, Service Models


# History
