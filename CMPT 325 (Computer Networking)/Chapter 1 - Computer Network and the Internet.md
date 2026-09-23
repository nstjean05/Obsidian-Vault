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
	- Propogration environment effectsL
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
		2. 270 msec end-end delay
