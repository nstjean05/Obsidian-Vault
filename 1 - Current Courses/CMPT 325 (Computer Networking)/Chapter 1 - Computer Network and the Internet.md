#incomplete 
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
- **Protocols** control sending and receiving of messages
- Standards:
	- RFC: Request for comments
	- IETF: Internet engineering task force
- As a service:
	- Major infrastructure providing services to apps for web streaming, email, games, e-commerce, etc.
## Network Edge
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
- **Access Network Types**
	1. Cable Based
		- Frequency Division Multiplexing: Different channels transmitted in different frequency bands
		- HFC: Hybrid fiber coax - high downstream transmission (1.2 Gbps), low upstream (100 Mbps) (1/10th)
		- Network of cable, fiber attaches homes to ISP router
	2. Digital Subscriber Line (DSL)
		- Used existing telephone line to central office DSLAM
			- Data over DSL phone line goes to internet
			- Voice over DSL phone line goes to telephone net
		- 24Mbps down, 3.5 Mbps upstream
	3. Home Networks
	4. Wireless Access Networks
		- WLAN: Wireless Local Area Network
			- 100ft range
			- 11/54/450 Mbps transmission
		- Wide-area cellular access network
			- Provided by mobile network operator
			- 10s of kms
			- 4G/5G cellular networks
	5. Enterprise Networks
		- Companies, universities, etc.
		- Mix of wired/wireless, switches/routers
		- Eth: 100Mbps, 1Gbps, 10Gbps
		- WiFi: 11, 54, 450 Mbps
	6. Data Center Networks
		- High-bandwidth links (10s-100s Gbps) connect 100s of servers together
- **Hosts**
	- Sends packets of data
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




1. Suppose that a packet-switched network is used and the only traffic in this network comes from such applications as described above. Furthermore, assume that the sum of the application data rates is less than the capacities of each and every link. Is some form of congestion control needed? Why?
Congestion control wouldn't be needed in this scenario, since each of the links has excess capacity. This means that there won't be any congestion to worry about.    

  
  

P7. In this problem, we consider sending real-time voice from Host A to Host B over a packet-switched network (VoIP). Host A converts analog voice to a digital 64 kbps bit stream on the fly. Host A then groups the bits into 56-byte packets. There is one link between Hosts A and B; its transmission rate is 10 Mbps and its propagation delay is 10 msec. As soon as Host A gathers a packet, it sends it to Host B. As soon as Host B receives an entire packet, it converts the packet’s bits to an analog signal. How much time elapses from the time a bit is created (from the original analog signal at Host A) until the bit is decoded (as part of the analog signal at Host B)?

17.04ms

P11. In the above problem, suppose R_1 = R_2 = R_3 = R and d_proc = 0. Further suppose that the packet switch does not store-and-forward packets but instead immediately transmits each bit it receives before waiting for the entire packet to arrive. What is the end-to-end delay?

d=L/R+d1/S1+d2/s2+d3/s3
L=1500 bytes
R=2.5Mbps
Prop speed 2.4•10$^8$ m/s
Links 5000, 4000, 1000km

L=1500bytes=12000bits
L/R=12000bites/2,500,000bits/s=0.0048s=4.8ms
Propogation = (5,000,000m/2.5•10^8)+(4,000,000m/2.5•10^8)+(1,000,000m/2.5•10^8) = 20 + 16 + 4 = 40ms

d=L/R+d1/S1+d2/s2+d3/s3
