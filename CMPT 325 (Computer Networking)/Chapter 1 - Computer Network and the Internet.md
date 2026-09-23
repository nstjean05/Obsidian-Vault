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
	- Faster, less overhead
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
	- Send packets of data
	- 