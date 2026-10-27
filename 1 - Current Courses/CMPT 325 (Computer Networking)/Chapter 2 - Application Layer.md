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
#### Review
- Web page consists of objects, each of which can be stored on different Web servers
- Object can be an HTML file, JPEG image, Java applet, audio, etc
- Web page consists of base HTML-file, which includes several referenced objects, each addressable by a URL, e.g.
	- www.someschool.ed/someDept/pic.gif
	-        Hostname                Path name
#### HTTP Overview
- Uses the client-server model
- Client is a browser that request, receives, and displays web objects using HTTP
- Server sends objects using HTTP in response to requests
- **HTTP uses TCP**
	1. Client init TCP connection to server, port 80
	2. Server accepts TCP connection from client
	3. HTTP messages (application layer protocol) exchanged between browser and Web server
	4. TCP connection closed
- HTTP is a stateless protocol
	- Server maintains no information about past client requests
	- Doesn't know about past steps
	- This keeps it simple, doesn't need to deal with cleanup on failure
#### HTTP Connection Types
- **Non-Persistent**
	1. TCP Connection Opened
	2. At most one object sent over TCP connectino
	3. TCP connection closes
	- Downloading multiple objects required multiple connections
- **Persistent HTTP**
	- TCP connection opened to a server
	- Multiple objects are sent over a single TCP connection between client and server
	- TCP connection is closed
	- This is HTTP v. 1.1, the most common type in use today
#### Non-Persistent HTTP Ex.
1. HTTP client initiates TCP connection @80, HTTP host accepts the TCO connection @80
2. HTTP client sends HTTP request message, indicating the desired object
3. HTTP server receives the request, forms a response message containing the object, sending it back into its socket to the client.
4. HTTP server closes TCP connection
5. HTTP client receives the response containing the HTML file, finding the referenced JPEG object
6. Repeat steps 1-5 for each of the 10 JPEG objects
- RTT (Round trip time)
	- Time needed for a very small packet to go client --> server --> client
![413](Pasted%20image%2020261026232258.png)
- **Response Time:** 2RTT + file transmission time
- **Issues**
	- Requires 2 RTTs per object
	- OS overhead for each TCP connection
	- Browsers often open multiple connections to fetch objects in parallel
#### Persistent HTTP Ex.
- HTTP 1.1
- Subsequent HTTP messages between same client and server are sent over an open connection
	- Server leaves connection open after sending response
- Client sends requests as soon as it encounters a referenced object
- As little as 1 RTT for all the referenced objects
#### HTTP Request Message
- Request starts with a single line
	- (Method name) (URL) (HTTP version) (carriage return char) (Newline)
	- Ex. GET /index.html HTTP/1.1\r\n
- Followed by a number of header lines, containing a lot of information about the host, user, language, encoding, etc.
	- Ended with a blank line (\r\n)
- General format:
![567](Pasted%20image%2020261026232916.png)
- As networking students, we don't have to know all these details
- Common HTTP request messages:
	- **POST**
		- Web page often includes form input
		- User input send from client to server in entity body of HTTP POST req message
	- **GET**
		- Sending data to a server
	- **HEAD**
		- Request headers (only) that would be returned *if* specific URL were requested with an HTTP GET method
	- **PUT**
		- Uploads a new file (object) to server
		- Completely replaces the file that exists at specified URL with content in entity body of POST HTTP GET message
#### HTTP Response Message
- Responds with the status line and code
- Followed with header lines, including added info
- Followed by the data of the document itself
- **Several status codes:**
	- 200 = OK
	- 301 = Moved Permanently
		- New location specified later in this message
	- 400 = Bad Request
	- 404 = Not Found
	- 505 = HTTP Version Not Supported
#### Cookies
- Allow websites and clients browser to maintain states between some interaction
- Four components:
	1. Cookie header line of HTTP response message
	2. Cookie header line in next HTTP *request* message
	3. Cookie file kept on user's host, managed by user's browser
	4. Back-end DB at Web site
- Example:
![](Pasted%20image%2020261026233816.png)
- There are many uses for cookies
	- Authentication
	- Recommendations
	- Shopping carts
	- User sessions state
- Challenges around cookies and privacy
	- Cookies permit sites to learn a lot about you on their site
	- Third party persistent tracking cookies
#### Web Caching
- Satisfies the clients requests without involving the origin server
- User configures a local browser to point to a local *web cache*
- Browser sends all HTTP req to cache
	- If object is in cache, it returns the object to the client
	- Else, cache request object, caches received object, then returns the object to the client
- Can act as both a client and a server
	- Server for original requesting client
	- Client to origin server
- Server tells cache about objects allowable caching in response header
	- If it can be cached
	- How long it can be cached for
- Reduces response time for request
- Reduce traffic
- Internet is dense with caches, allowing worse providers better service
#### Caching Example
- Access link rate of 1.54 MBPS
- RTT from institutional router to server: 2 sec
- Web object size: 100K bits
- Avg request rate from browsers to origin: 15/sec
	- Avg data rate to browsers: 1.5 Mbps
- **Performance**
	- Access link utilization: 0.97
	- LAN utilization: 0.0015
	- end-end delay = internet delay + access link delay + LAN delay = 2s + min + u secs
- Possible upgrades
	- Upgrade accessing link to 154 Mbps, lowering utilization
	- Local web cache
- **With Cache**
	- Suppose cache hit rate is 0.4
		- 40% of requests served by cache, with very low delay
	- 60% requests satisfied at origin
		- Rate to browsers over access link
			- = 0.6 • 1.5 Mbps = 0.9 Mbps
		- Access link utilization = 0.9/1.54 - 0.58
			- Low (msec) queuing delay at access link
	- Average end-end delay
		- = 0.6 • delay from origin + 0.4 • delay from cache = 0.6(2.01) + 0.4(msecs) = ~1.2 secs
	- Lowers the average end to end delay, without breaking the bank
#### Conditional GET
- Alternative caching method
- Don't send object if cache already has an up to date version
	- No object transmission delay
- Client will specify the date of cached copy in HTTP request
- Server will send an empty response if the cached copy is up to date
	- 304 Not Modified
- If not up to date, sends 200 OK
#### HTTP/2
- Goal of decreasing delay in multi-object HTTP requests
- Objects get priority, not just FIFO
- Additional info like status codes, extra methods
- Push unrequested methods to client
- Large objects are split into frames, and can be mixed in with other objects
	- Gets more objects transmitted faster
#### HTTP/3
- Added security
- Per-object error and congestion control over UDP
# 2.3 Email
- 3 Major components
	1. User agents
	2. Mail servers
	3. Simple mail transfer protocol (SMTP)
- **User Agents**
	- a.k.a. mail reader
	- Composing, editing, reading mail messages
	- Outlook, Gmail, etc.
	- Outgoing and incoming messages are stored on a server
- **Email Servers**
	- Mailbox containing incoming messages for user
	- Message queue of outgoing mail messages
	- SMTP Protocol between mail servers to send email messages
		- Client: sending mail server
		- Server: receiving mail server
#### Example Email
1. Alice uses gmail to compose email message to bob@someschool.edu
2. Alice's gmail sends message to her mail server using SMTP; message placed in message queue
3. Client side of SMTP at mail server opens TCP connection with Bob's mail server
4. SMTP client sends Alice's message over the TCP connection
5. Bob's mail server places the message in Bob's mailbox
6. Bob invokes his user agent to read message
![](Pasted%20image%2020261027000522.png)
#### SMTP RFC 5321
- Uses TCP to reliably transfer email message from client to server, port 25
- Email messages are transferred directly from sending to receiving servers
- Three phases of transfer:
	1. SMPT handshaking (greeting)
	2. SMTP transfer of message
	3. SMTP closure
- Command/response interaction (like HTTP)
	- Commands: ASCII text
	- Response: Status code and phrase
#### SMTP Observations
- HTTP: Client Pull
- SMTP: Client Push
- Both have ASCII command/response interaction, status codes
- HTTP: each object is encapsulated in its own response message
- SMTP: multiple objects sent in multipart message
- SMTP: Persistent connections
- SMTP: Requires messages in 7-bit ASCII
	- Terminated with a line with only a period
- SMTP: protocol for exchanging email messages, defined in RFC 5321
	- Header lines
	- To:
	- From:
	- Subject:
	- Contents:
#### Retrieving Email
- SMTP - Delivery and storage of email to receiver server
- IMAP - Internet Mail Access Protocol
	- Messages stored on server, IMAP provides retrieval, deletion, folders of stored messages on the server
- HTTP - gmail, hotmail, Yahoo, etc.
	- Provides a web-based interface on top of SMTP (to send), IMAP (or POP) to retrieve
# 2.4 - Domain Name System (DNS)
- DNS is able to distribute its services at scale with relative efficiency
- It is an application-layer service, using TCP and UDP
#### DNS Structure & Function
- DNS is all about names and identifiers
	- *People* have many such identifiers, SSN, name, passport number
	- *Internet hosts and routers* have identifiers too
		- IP address, used to address datagrams
		- Name, used by humans (URL)
- **DNS**
	- Distributed DB implemented in hierarchy of many name-servers
	- Application layer protocol: hosts, DNS servers communicate to resolve names (address/name translation)
	- Core internet function, implemented as application layer protocol
	- Complexity at network's edge (rather than routers and switches in the network)
		- This is a consistent design philosophy
- **DNS Services and Structure**
	- Services
		- Hostname-to-IP-address translation
		- Host aliasing
			- Canonical, alias names
		- Mail server aliasing
		- Load distribution
- Why not a central approach:
	- Single point of failure
	- Traffic volume
	- Distant central DB (slow)
	- Maintenance
- DNS is an enormous distributed database
- Handles trillions of queries per day
- Very decentralized
	- Millions of different organizations responsible for their records
#### A Hierarchical DB
- Root DNS servers direct to top-level domains, followed by authoritative domains
- Ex. Client wants IP address for www.amazon.com
	1. Client queries the root server to find .com DNS server
	2. Client queries .com DNS server to get amazon.com DNS server
	3. Client queries amazon.com DNS server to get IP address for amazon.com
- **Root Servers**
	- Official, contact of last resort by name servers that cannot resolve a name
	- Incredible important internet function, without which everything would break
	- DNSSEC provides security
	- ICANN - Internet Corporation for Assigned Names and Numbers
		- Manage root DNS domain
- **Top Level Domain (TLD)**
	- Each of the root servers at the top level domain is responsible for resolving one of the addresses of a TLD server (.com, .net, etc.)
	- Country level domains, .us, .ca, .fr, etc.
- **Authoritative DNS Servers**
	- Organization's own DNS server(s), providing authoritative hostname to IP mappings for orgs named hosts
	- Can be maintained by organization or service provider
![](Pasted%20image%2020261027113300.png)
- **Local DNS Server**
	- When host makes a DNS query, it is sent to its local DNS server
	- Local DNS server returns reply, answering:
		- From its local cache of recent name-address translation pairs
		- Forwarding request into DNS hierarchy for resolution
	- Each ISP has a local DNS name server
		- MacOS: % scutil --dns
		- Windows: >ipconfig /all
#### Resolving DNS Queries
- **Iterated query**
	- Contacted server replies with name of server to contact
		- "I don't know this name, but ask this server"
	- This uses a lot of traffic, and DNS caching can speed this up
![380](Pasted%20image%2020261027113749.png)
- **Recursive Query**
	- Puts burden of name resolution on contacted name server
	- Heavy load at upper levels of the hierarchy
![377](Pasted%20image%2020261027113947.png)
#### Caching DNS Information
- Once any name server learns mapping, it caches mapping, and immediately returns a cached mapping in response to a query
	- Improves response time
	- Cache entries time out (TTL - time to live)
	- TOLD servers usually cached in local name servers
- Cached entries may be out of date
	- If named host changes the IP address, may not be known internet wide until all TTLs expire
	- Best-effort name to address translation
	- No need for a costly and complicated mechanism to purge info from caches
#### DNS Records
- DNS: Distributed database storing resource records (RR)
	- RR Format: name, value, type, ttl
- Type = A
	- Name is hostname
	- Value is IP address
- Type = NS
	- Name is domain
	- *Value* is hostname of authoritative name server for this domain
- Type = CNAME
	- Name is alias name for some canonical name
		- Ex. www.IBM.com is really servereast.backup2.ibm.com
- Type = MX
	- Value is the name of SMTP mail server associated with the name
#### DNS Protocol Messages
- DNS query and reply messages, both with the same format
- Header includes ID info, and flags for query/reply, recursion, etc.
![238](Pasted%20image%2020261027114640.png)
#### Example - Get you info into the DNS
- New startup *Network Utopia*
	- Register name *networkutopia.com* at DNS registrar
		- Provide names, IP addresses of authoritative name server
		- Registrar inserts NS, a RRs into .com TLD server
#### DNS Security
- DDoS
	- Bombard root servers with traffic
		- Not successful to date
		- Traffic filtering
		- Local DNS servers cache IPs of TOLD servers, allowing root server bypass
	- Bombard TLS servers
		- Potentially more dangerous
# 2.6 Video Streaming, CDNs
- 80% of residential ISP traffic goes to video
- Challenges of scale (reaching 1B users) and heterogeneity (different users with different capabilities)
	- Solution: distributed, application level infrastructure.
#### Video
- Coding: Use redundancy within or between frames to decrease the number of bits used to encode each image
- **CBR**
	- Constant bit rate video
	- Fixed encoding rate
- **VBR**
	- Variable bit rate
	- Encoding rate changes as amount of spatial and temporal coding changes
- Examples
	- MPEG 1, 1.5 Mbps, CD-ROM
	- MPEG 2, 3-6 Mbps, DVD
	- MPEG 4, 65Kbps-12Mbps, Internet
#### Streaming Stored Video
- Bandwidth between client and server will vary over time
- Packet loss and delay due to congestion with delay play, or decrease video quality
	1. Video is recorded
	2. Sent by server
	3. Played by client
- Frames are sent in the order they were recorded
- Video can still be filmed, sent, and played all at the same time
	- Client playing an earlier part while server is sending a later part
- Continuous play-out constraint:
	- During client video playout, playout timing must match original timing
	- But network delays are variable
	- Buffering can be used to absorb some of the changes in delay
- Other challenges
	- Client interactivity (pause, fast forward, etc.)
	- Video packets may be lost and retransmitted
![543](Pasted%20image%2020261027120352.png)
- You want to buffer as little video as possible, without dropping service
#### Streaming multimedia: DASH
- When buffering isn't enough to feed the client all the data they're asking for
- DASH - Dynamic, Adaptive Streaming over HTTP
- **Server**
	- Divides video into chunks
	- Chunks encoded at different rates
	- Different rate encodings stored in different files
	- Files replicated in various CDN (server) nodes
	- Manifest file: provides URLs for different chunks
- **Client**
	- Periodically estimate the amount of server-client bandwidth
	- Consulting manifest, requesting one chunk at a time
		- Chooses the maximum coding rate sustainable given current bandwidth
		- Can choose various encoding rates at different points, and from different servers
- *Intelligence* at client determines:
	- When to request chunk
	- What encoding rate to request
	- Where tor request chunk from
#### Content Distribution Networks (CDNs)
- How to stream contents from millions of videos, to hundreds of thousands of simultaneous users
1. Single, large, mega-server
	- Single point of failure
	- Congestion
	- Long path to distant clients
	- Poor scaling
2. Distributed Infrastructure (CDN)
	- Store and server multiple copies of videos at multiple geographically distributed sites
	- 2 Approaches to CDN
	1. **Enter Deep**
		- Push CDN servers deep into many access networks
		- Close to users
	2. **Bring Home**
		- Small number (10s) of larger clusters in POPs near access nets
- Streaming video via CDN
	- CDN stores copies of content at CDN nodes
	- Subscriber requests content, service provider returns manifest
		- Using manifest, client retrieves content at highest supportable rate
		- May choose a diff rate or copy if network path congested
- OTT: Over the top
	- An application level service, running on top of the ISP infrastructure
# 2.6 - Socket Programming