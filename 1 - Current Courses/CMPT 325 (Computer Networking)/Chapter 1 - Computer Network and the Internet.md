#incomplete 
# Videos
- 1.1 - https://www.youtube.com/watch?v=74sEFYBBRAY
	- Intro
- 1.2 - https://www.youtube.com/watch?v=k8NmM-hImBU
	- Network Edge
- 2.3 - https://www.youtube.com/watch?v=f1nUcCdQJ8Y&list=PL1ya5dD_M8uX-BLUF1FEvUNsYWQL5_l0O&index=3
	- Network Core
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
#### Wireless Access Networks
1. Wireless Access Networks
	- WLAN: Wireless Local Area Network
		- 100ft range
		- 11/54/450 Mbps transmission
	- Wide-area cellular access network
		- Provided by mobile network operator
		- 10s of kms
		- 10s Mbps
		- 3G/4G/5G cellular networks
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
	- **Bit**: Propagates between transmitter/receiver pairs
	- **Physical Link:** What lies between the transmitter and receiver
	- **Guided Media:** Signals propagate in solid media (e.g. copper, fiber, coax, etc.)
	- **Unguided Media:** Signals propagate freely (e.g. radio)
- **Coaxial Cable** (Twister Pair, TP)
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
	- Expensive
- **Wireless Radio**
	- Signal carried in various bands in electromagnetic spectrum
	- No physical wire
	- Broadcast
		- Any device near the receiver can also receive the message
	- Propagation environment effects
		- Reflection
		- Obstruction by objects
		- Interference/noise
	- Requires a lot of work at the physical layer
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
#### Links: Physical Access Media
# Network Core
- Interconnected routers
	- A network of networks
- **Packet switching:** Hosts break application-layer messages into packets
	- Forward packets from one router to the next, across links on the path
	- Each packet is transmitted at full capacity
- Fundamental Q: How is data transferred on the net?
	- **Packet Switching:** Sent through the net in discrete chunks
	- **Circuit Switching:** Dedicated circuit for each call
- Forwarding --> "Switching"
	- Low-level passing of info between routers
#### Packet Switching
- Transmission delay: Takes L/R seconds to transmit L-bit packets into link at R bps
- Store and forward: entire packet must arrive at router before it can be transmitted on
- End-end Delay: 2L/R, assuming zero propagation delay
- Forwarding is a local action - moving arriving packets from routers input to output links
- Routing is a global action - determining source destination paths that packets traverse
	- Uses routing algos (Dijkstra)
- Queuing occurs when work arrives faster than it can be serviced
- Packet queuing and loss
	- If arrival rate in bops
- Packet loss can happen when the delays get too big
#### Circuit Switching
- Alternative to packet switching
- No delay other than propagation delay
- End-end resources are allocated and reserved for the call between source and destination
- However, even if the circuit isn't full, 
#### Examples
- How many users can use a network under circuit vs packet switching?
- Given:
	- 1 Gb/s link
	- Each user:
		- 100 Mb/s when 'active'
		- Active 10% of time
		- N users
- Circuit switching: 10 users
- Packet switching, with 35 users, probability of > 10 active users at the same time is less than 0.0004%
	- In some sense, packet switching could be declared the winner
#### Internet Structure
- A network of networks
- Given millions of access ISPs, how can they be connected?
	1. A global ISP that all ISPs are connected to
	2. Broke into multiple global ISPs that compete
		- A couple IXPs that connect the globals
	3. Connected provider network
		- Large companies like Google and Amazon who have national and international coverage
	- All 3 of these levels overlap to the current internet
- POP: Point of presence to and from other PoPs
	- Ex. Verizon
		- Lowest level: links to customer networks
		- Customer networks link up to PoPs
		- PoPs can link to peering networks and other PoPs
# Performance
#### Sources of Packet Delay
- **Nodal Processing**
	- Check for bit errors
	- Determine the output link
	- Typically < microseconds
- **Queuing Delay**
	- Time waiting at the output link for transmission
	- Depends on the congestion level of the router
- **Transmission Delay**
	- L: Packet length (bit)
	- R: Link transmission rate (bps)
	- d_trans = L/R
- **Propagation Delay**
	- d: Length of physical link
	- s: propagation speed (~2•10^8 m/sec)
	- d_prop = d/s
- Total delay is the sum of these
#### Real Internet Delay and Routes
- *Traceroute* is a program the provides delay measurement from source to router along end-end internet path towards the destination
	- For all i:
		- Send 3 packets that will reach router i on path towards destination
		- Router i will return packets to the sender
		- Sender measures time interval between transmission and reply
#### Packet Loss
- Queue (buffer) - Preceding link in buffer has finite capacity
- Packet arriving to a full queue dropped (lost)
- Lost packet may be retransmitted by a previous node, by source end system, or not at all
#### Throughput
- Rate in bits per second at which bits are being sent from sender to receiver
	- Instantaneous: rate at given point in time
	- Average: rate over longer period of time
- Steps:
	1. Server sends bits (fluid) into pipe
	2. Pipe that can carry fluid at a rate of R1 bits/s
	3. Arrives at first link
	4. Pipe that can carry fluid at rate R2 bits/s'
	5. Arrives at endpoint
- Average throughput is limited to the the smaller pipe, whether R1 or R2
	- Bottleneck link
![](Pasted%20image%2020261026215419.png)
- A network scenario:
![](Pasted%20image%2020261026215448.png)
- You can imagine it as three pipes going through one main pipe and splitting back into three
- Let's say that R has a fair share between 10 connections at R bits/s
	- Per connection end-end throughput
		- min(R$_C$, R$_S$, R / 10)
	- In practice: R$_C$ or R$_S$ is smaller than R/N
		- Bottleneck link is therefore at the network edge
- Bottlenecks tend to be at the edge of the network.
# Layering, Services, & Encapsulation
- Airline travel is a good example of a frequently used complex system
	- It can be thought of a series of steps
	- Ticket, baggage, gates, takeoff, etc...
	- Flight
	- Landing, gates, baggage, departure
	- Each has its match on the other end of the trip (layers)
- Layered internet protocol stack
	1. Application: supporting network applications (HTTP, IMAP, SMTP, DNS)
	2. Transport: Process-process data transfer (TCP, UDP)
	3. Network: Routing of datagrams from source to destination (IP, routing protocols)
	4. Link: Data transfer between neighbouring network elements (ethernet, 802.11 WiFi, PPP)
	5. Physical: 'Bits on the wire'






# Security


# Protocol Layers, Service Models


# History
