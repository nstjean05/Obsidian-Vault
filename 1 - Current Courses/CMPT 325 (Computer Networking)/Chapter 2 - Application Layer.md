### 2.1 Principles of Network Applications
#### 2.1.1 Creating a network app
- Write programs that run on (different) **end systems** and communicate over the network
    - Ex. web server software talks to browser software
- No need to write software for **network-core devices**
    - Core devices don’t run user apps
    - Apps on end systems = rapid development and propagation
- Ex. apps: social networking, Web, text messaging, e-mail, multi-user games, streaming stored video, P2P file sharing, VoIP, video conferencing, search, remote login
#### 2.1.2 Application architectures

1. **Client-server**
    - **Server**: always-on host, permanent IP, often in data centres for scaling
    - **Clients**: contact the server, may be intermittently connected, may have dynamic IPs
    - Clients _do not_ talk directly to each other
    - Heavily used service = group of servers, not just one
    - Ex. HTTP, IMAP, FTP, web, file servers, e-mail
2. **Peer-to-peer (P2P)**
    - No always-on server, arbitrary end systems communicate directly
    - Peers request service from peers and provide service in return
    - **Self scalability**: new peers bring new capacity _and_ new demand
    - Peers intermittently connected, change IPs = complex management
    - Decentralized, hard to guarantee reliable service
        - Ex. if only one host has the info and it leaves, info is lost
    - Ex. BitTorrent, KanKan, Skype
3. **Hybrid** systems have both client-server and P2P aspects

#### 2.1.3 Processes communicating

- **Process** is a program running within a host
    - Same host: processes use **inter-process communication** (defined by OS)
    - Different hosts: processes exchange **messages**
- **Client process** initiates communication, **server process** waits to be contacted
    - P2P apps have both client and server processes
- **Socket** is the “door” between process and transport layer
    - Sending process shoves message out the door, relies on transport infrastructure on the other side to deliver to the receiving socket
    - Two sockets involved, one on each side
    - Controlled by OS (transport and below) vs app developer (application side)

#### 2.1.4 Addressing processes

- To receive messages, a process needs an **identifier**
- Host has unique 32-bit **IP address**
    - Not enough alone, many processes can run on one host
- Identifier = **IP address + port number**
    - HTTP server: port 80
    - Mail server: port 25
    - Ex. gaia.cs.umass.edu web server = 128.119.245.12, port 80

#### 2.1.5 App-layer protocol defines

- Types of messages exchanged (ex. request, response)
- **Message syntax**: what fields, how delineated
- **Message semantics**: meaning of info in fields
- Rules for when and how processes send and respond
- **Open protocols**: defined in RFCs, allow interoperability (ex. HTTP, SMTP)
- **Proprietary protocols** (ex. Skype)

#### 2.1.6 Transport service needs

- **Data integrity**
    - File transfer, web transactions need 100% reliable transfer
    - Audio can tolerate some loss
- **Timing**
    - Internet telephony, interactive games need low delay to be “effective”
- **Throughput**
    - Multimedia needs a minimum amount
    - **Elastic apps** use whatever they get
- **Security**
    - Encryption, data integrity, etc.

Common apps:

- File transfer/download: no loss, elastic, not time sensitive
- E-mail: no loss, elastic, not time sensitive
- Web documents: no loss, elastic, not time sensitive
- Real-time audio/video: loss-tolerant, audio 5 Kbps to 1 Mbps, video 10 Kbps to 5 Mbps, time sensitive (10’s msec)
- Streaming audio/video: loss-tolerant, same rates, time sensitive (few secs)
- Interactive games: loss-tolerant, Kbps+, time sensitive (10’s msec)
- Text messaging: no loss, elastic, yes and no

#### 2.1.7 Internet transport protocols

- **TCP** service
    - Reliable transport between sending and receiving process
    - **Flow control**: sender won’t overwhelm receiver
    - **Congestion control**: throttles sender when network is overloaded
    - **Connection-oriented**: setup needed between client and server
    - Does _not_ provide timing, minimum throughput, security
- **UDP** service
    - Unreliable data transfer
    - No reliability, flow control, congestion control, timing, throughput guarantee, security, or connection setup
    - _Why bother with UDP?_ Low overhead, no setup delay, no throttling
- Which app uses what
    - FTP: TCP
    - SMTP: TCP
    - HTTP: TCP
    - Internet telephony (SIP, RTP, or proprietary): TCP or UDP
    - Streaming (HTTP, DASH): TCP
    - Interactive games (WOW, FPS, proprietary): UDP or TCP

#### 2.1.8 Securing TCP

- Vanilla TCP and UDP sockets have **no encryption**
    - Cleartext passwords sent into socket cross the Internet in cleartext (!)
- **Transport Layer Security (TLS)**
    - Encrypted TCP connections
    - Data integrity
    - End-point authentication
- TLS is implemented in the **application layer**
    - Apps use TLS libraries, which use TCP in turn
    - Cleartext into socket = encrypted across the Internet
    - Covered in Ch. 8

### 2.2 Web and HTTP

#### 2.2.1 HTTP overview

- Web page = objects, each can be on a different server
    - Object can be HTML file, JPEG, Java applet, audio file, etc.
    - Base HTML file references other objects, each addressable by a **URL**
    - Ex. [www.someschool.edu/someDept/pic.gif](http://www.someschool.edu/someDept/pic.gif) = **host name** + **path name**
- **HTTP** (hypertext transfer protocol) is the Web’s app-layer protocol
    - Client = browser that requests, receives, displays objects
    - Server = Web server that sends objects in response to requests
- HTTP uses **TCP**
    1. Client initiates TCP connection (creates socket) to server, port 80
    2. Server accepts
    3. HTTP messages exchanged
    4. TCP connection closed
- HTTP is **stateless**
    - Server keeps no info about past client requests
    - Stateful protocols are complex
        - Past history must be maintained
        - If server/client crashes, their views of state may be inconsistent and must be reconciled

#### 2.2.2 HTTP connections

- **Non-persistent HTTP**
    
    1. TCP connection opened
    2. At most one object sent
    3. TCP connection closed
    
    - Multiple objects = multiple connections
- **Persistent HTTP** (HTTP 1.1)
    - TCP connection opened to a server
    - Multiple objects sent over the single connection
    - Server leaves connection open after sending response
    - Client sends requests as soon as it finds a referenced object
    - As little as one RTT for all referenced objects
- Non-persistent issues
    - 2 RTTs per object
    - OS overhead for each TCP connection
    - Browsers often open parallel connections to compensate

#### 2.2.3 Response time

- **RTT** is time for a small packet to go client to server and back
- Non-persistent HTTP response time per object:
    1. One RTT to initiate TCP connection
    2. One RTT for HTTP request and first few bytes of response
    3. File transmission time
- **Response time = 2 RTT + file transmission time**
- Persistent saves one RTT per object (cuts response time in half)

#### 2.2.4 HTTP request message

- Two types of messages: request, response
- ASCII (human-readable)
- Parts
    - **Request line**: method, URL, version
    - **Header lines**: header field name, value
    - Blank line (CR LF) ends the headers
    - **Entity body** (optional)
- Ex. `GET /index.html HTTP/1.1` then `Host:`, `User-Agent:`, `Accept:`, `Accept-Language:`, `Connection: keep-alive`
- Methods
    - **GET**: request an object
        - Can send data in the URL after a `?`
        - Ex. [www.somesite.com/animalsearch?monkeys&banana](http://www.somesite.com/animalsearch?monkeys&banana)
    - **POST**: form input goes in the entity body
    - **HEAD**: requests headers only (what a GET would return)
    - **PUT**: uploads a new file, _completely replaces_ file at that URL with entity body

#### 2.2.5 HTTP response message

- Parts
    - **Status line**: protocol, status code, status phrase
    - Header lines (Date, Server, Last-Modified, Content-Length, Content-Type, etc.)
    - Data (ex. requested HTML file)
- Status codes (1st line of server-to-client response)
    - **200 OK**: success, object later in message
    - **301 Moved Permanently**: new location in `Location:` field
    - **400 Bad Request**: msg not understood
    - **404 Not Found**: document not on this server
    - **505 HTTP Version Not Supported**
- Try it yourself
    - `telnet gaia.cs.umass.edu 80`
    - Type a GET request plus `Host:` line, hit return twice
    - Or use Wireshark to capture request/response

#### 2.2.6 Cookies

- HTTP is stateless, so sites use **cookies** to keep state between transactions
- Four components
    1. Cookie header line in HTTP response
    2. Cookie header line in next HTTP request
    3. Cookie file kept on user’s host, managed by browser
    4. Back-end database at the site
- How it works
    - First visit: site creates unique ID and a database entry for it
    - Response has `Set-cookie: 1678`
    - Later requests include `Cookie: 1678`, so the site can “identify” the user
- Uses
    - Authorization
    - Shopping carts
    - Recommendations
    - User session state (Web e-mail)
- **First party cookie** comes from the site you chose to visit
- **Third party cookie** comes from a site you did _not_ choose to visit
    - Ex. ad server embedded in nytimes.com
    - Tracks browsing across sites with that ad network
    - Can be invisible to the user (invisible link instead of a displayed ad)
    - Disabled by default in Firefox and Safari, Chrome planned to follow
- **GDPR**
    - Cookies that can identify an individual are _personal data_
    - User has explicit control over whether cookies are allowed
- Aside: this is why cookie banners are everywhere

#### 2.2.7 Web caches (proxy servers)

- Goal: satisfy client request _without_ involving the origin server
- Browser points to the cache
    - Object in cache: cache returns it
    - Else: cache requests from origin, stores it, returns to client
- Cache acts as both client (to origin) and server (to original client)
- Usually installed by an ISP (university, company, residential)
- Why caching
    - Lower response time (cache is closer)
    - Reduces traffic on an institution’s access link
    - Lets “poor” content providers deliver content more effectively

#### 2.2.8 Caching example

- Scenario
    - Access link rate: 1.54 Mbps
    - RTT institutional router to server: 2 sec
    - Object size: 100K bits
    - Request rate: 15/sec
    - Avg data rate to browsers: 1.50 Mbps
- No fix
    - LAN utilization .0015
    - **Access link utilization .97** = huge delays (minutes)
- Option 1: buy a faster link (154 Mbps)
    - Utilization .0097, delay = 2 sec + msecs
    - Expensive!
- Option 2: **install a web cache** (cheap!)
    - Hit rate 0.4: 40% served at cache, 60% go to origin
    - Access link data rate = 0.6 × 1.50 = .9 Mbps
    - Utilization = 0.9 / 1.54 = **.58**
    - Avg delay = 0.6 (2.01) + 0.4 (~msecs) ≈ **1.2 secs**

#### 2.2.9 Conditional GET

- Goal: don’t send the object if cache already has an up-to-date copy
    - No transmission delay, lower link utilization
- Cache specifies date of its copy: `If-modified-since: <date>`
- Server response
    - Up to date: `304 Not Modified`, no object
    - Modified: `200 OK` with the data

### 2.3 E-mail, SMTP, IMAP

#### 2.3.1 Components

- Three major parts
    1. **User agents** (mail reader, ex. Outlook, iPhone mail)
    2. **Mail servers**
    3. **SMTP**
- **User agent**: composing, editing, reading messages
    - Outgoing and incoming messages stored on server
- **Mail server**
    - **Mailbox** holds incoming messages for the user
    - **Message queue** of outgoing mail
    - SMTP between mail servers
        - Sending server = “client”
        - Receiving server = “server”

#### 2.3.2 SMTP (RFC 5321)

- Uses **TCP**, port 25
- **Direct transfer**: sending server to receiving server
- Three phases
    1. Handshaking (greeting)
    2. Transfer of messages
    3. Closure
- Command/response interaction like HTTP
    - Commands: ASCII text
    - Responses: status code and phrase
- Alice to Bob scenario
    1. Alice composes message to [bob@someschool.edu](mailto:bob@someschool.edu) in her UA
    2. UA sends it to her mail server, placed in queue
    3. Client side of SMTP opens TCP connection to Bob’s mail server
    4. SMTP client sends Alice’s message over the connection
    5. Bob’s mail server puts it in Bob’s mailbox
    6. Bob invokes his UA to read it
- Sample interaction
    - `S: 220 hamburger.edu`
    - `C: HELO crepes.fr`
    - `C: MAIL FROM:` then `RCPT TO:` then `DATA`
    - Message ends with `.` on a line by itself
    - `C: QUIT`
- Try it: `telnet <servername> 25`
    - Only works if server allows it (increasingly rare, security)
- Closing observations
    - **Persistent** connections
    - Message (header and body) must be **7-bit ASCII**
    - Server uses **CRLF.CRLF** to detect end of message
- **SMTP vs HTTP**
    - HTTP is **pull**, SMTP is **push**
    - Both: ASCII command/response, status codes
    - HTTP: each object in its own response
    - SMTP: multiple objects in one multipart message

#### 2.3.3 Mail message format

- SMTP exchanges messages, **RFC 822** defines the message syntax (like HTML)
- Header lines: To:, From:, Subject:
    - _Different_ from SMTP MAIL FROM:, RCPT TO: commands!
- Blank line, then body (ASCII only)

#### 2.3.4 Mail access protocols

- **SMTP**: delivery and storage to the receiver’s server
- **Mail access protocol**: retrieval from the server
    - **IMAP** (RFC 3501): messages stay on the server, provides retrieval, deletion, folders
    - **HTTP**: Gmail, Hotmail, Yahoo!Mail give a web interface on top of SMTP (send) and IMAP or POP (retrieve)

### 2.4 The Domain Name System (DNS)

#### 2.4.1 Services

- Hosts have IP addresses (32 bit, for datagrams) and names (ex. cs.umass.edu, for humans)
- **DNS** is a distributed database implemented in a hierarchy of many name servers
    - Also an app-layer protocol: hosts and name servers communicate to resolve names
    - Core Internet function, but complexity sits at the network’s “edge”
- Services
    - Hostname to IP translation
    - **Host aliasing** (canonical and alias names)
    - Mail server aliasing
    - **Load distribution** (many IPs for one name on replicated web servers)
- _Why not centralize DNS?_
    - Single point of failure
    - Traffic volume
    - Distant centralized database
    - Maintenance
    - Doesn’t scale (Comcast DNS servers alone: 600B queries per day)
- Properties
    - ~ billion records, many trillions of queries/day
    - Many more reads than writes
    - Performance matters, msecs count
    - Organizationally and physically decentralized
    - “Bulletproof”: reliability, security

#### 2.4.2 Hierarchy

- Three levels
    1. **Root** DNS servers
    2. **Top-Level Domain (TLD)** servers (.com, .org, .edu)
    3. **Authoritative** servers (ex. amazon.com DNS servers)
- First approximation for [www.amazon.com](http://www.amazon.com)
    1. Ask root for the .com TLD server
    2. Ask .com TLD for the amazon.com authoritative server
    3. Ask authoritative server for the IP of [www.amazon.com](http://www.amazon.com)
- **Root name servers**
    - Contact of last resort for names others can’t resolve
    - Internet couldn’t function without them
    - **DNSSEC** gives authentication and message integrity
    - **ICANN** manages the root DNS domain
    - **13 logical** root “servers”, each replicated many times
- **TLD servers**
    - Handle .com, .org, .net, .edu, .aero, .jobs, .museums, and country domains (.cn, .uk, .fr, .ca, .jp)
    - Network Solutions: registry for .com, .net
    - Educause: .edu
- **Authoritative servers**
    - Organization’s own DNS server(s) with authoritative hostname to IP mappings
    - Maintained by the org or a service provider
- **Local DNS name server**
    - Doesn’t strictly belong to the hierarchy
    - Each ISP has one (the “default name server”)
    - Host queries go to it first
    - Acts as proxy, forwards into the hierarchy
    - Has a local cache (may be out of date!)

#### 2.4.3 Name resolution

- **Iterated query**
    - Contacted server replies with the name of the next server to contact
    - “I don’t know this name, but ask this server”
    - Ex. engineering.nyu.edu looking for gaia.cs.umass.edu: local DNS asks root, then TLD, then authoritative in turn
- **Recursive query**
    - Puts the burden of resolution on the contacted server
    - Heavy load at upper levels of the hierarchy?

#### 2.4.4 Caching

- Once any name server learns a mapping, it **caches** it and returns it right away
    - Improves response time
    - Entries time out after a **TTL**
    - TLD servers typically cached in local name servers
- Cached entries may be **out of date**
    - If a host changes IP, not known Internet-wide until all TTLs expire
    - Best-effort name-to-address translation

#### 2.4.5 DNS records

- Resource records (RR) format: **(name, value, type, ttl)**
- **type=A**: name is hostname, value is IP address
- **type=NS**: name is domain (ex. foo.com), value is hostname of authoritative name server
- **type=CNAME**: name is alias, value is canonical (real) name
    - Ex. [www.ibm.com](http://www.ibm.com) is really servereast.backup2.ibm.com
- **type=MX**: value is name of SMTP mail server for that name

#### 2.4.6 DNS protocol messages

- Query and reply have the _same format_
- Header
    - **Identification**: 16 bit #, reply uses the same #
    - **Flags**: query or reply, recursion desired, recursion available, reply is authoritative
- Sections
    - Questions (name, type fields for a query)
    - Answers (RRs in response)
    - Authority (records for authoritative servers)
    - Additional info (“helpful” extras)

#### 2.4.7 Getting your info into DNS

- Ex. startup “Network Utopia”
    1. Register the name at a **DNS registrar** (ex. Network Solutions)
        - Provide names and IPs of authoritative name servers (primary and secondary)
        - Registrar inserts NS and A RRs into the .com TLD server
            - (networkutopia.com, dns1.networkutopia.com, NS)
            - (dns1.networkutopia.com, 212.212.212.1, A)
    2. Create the authoritative server locally (212.212.212.1)
        - Type A record for [www.networkutopia.com](http://www.networkutopia.com)
        - Type MX record for networkutopia.com

#### 2.4.8 DNS security

- **DDoS attacks**
    - Bombard root servers: not successful so far
        - Traffic filtering
        - Local DNS servers cache TLD server IPs, so root can be bypassed
    - Bombard TLD servers: potentially more dangerous
- **Redirect attacks**
    - Man-in-the-middle: intercept DNS queries
    - **DNS poisoning**: send bogus replies to a DNS server, which caches them
- **Exploit DNS for DDoS**
    - Send queries with spoofed source address (target IP)
    - Requires amplification
- Defence: **DNSSEC** (RFC 4033)

### 2.5 P2P Applications

#### 2.5.1 File distribution: client-server vs P2P

- Question: time to distribute file of size F from one server to N peers?
- Terms
    - $u_s$: server upload capacity
    - $u_i$: peer i upload capacity
    - $d_i$: peer i download capacity
    - Peer upload/download capacity is the limited resource
- **Client-server**
    - Server must sequentially upload N copies: time $NF/u_s$
    - Each client must download the file: time $F/d_{min}$
    - $D_{c-s} \geq \max\{NF/u_s,\ F/d_{min}\}$
    - **Increases linearly in N**
- **P2P**
    - Server uploads at least one copy: time $F/u_s$
    - Each client must download: time $F/d_{min}$
    - Clients as an aggregate must download NF bits, max aggregate upload rate is $u_s + \sum u_i$
    - $D_{P2P} \geq \max\{F/u_s,\ F/d_{min},\ NF/(u_s + \sum u_i)\}$
    - Also linear in N, _but_ each peer brings service capacity
- Example: client upload rate u, F/u = 1 hour, $u_s$ = 10u, $d_{min} \geq u_s$
    - Client-server min distribution time climbs linearly with N
    - P2P levels off, stays near 1 hour

#### 2.5.2 BitTorrent

- File divided into **256 Kb chunks**
- **Torrent**: group of peers exchanging chunks of a file
- **Tracker**: tracks peers participating in the torrent
- Joining peer
    - Has no chunks, accumulates them over time
    - Registers with the tracker for a list of peers, connects to a subset (**neighbours**)
    - Uploads chunks to others _while_ downloading
    - May change peers it exchanges with
- **Churn**: peers come and go
- Once a peer has the whole file it may (selfishly) leave or (altruistically) stay
- **Requesting chunks**
    - Different peers have different subsets
    - Periodically ask each peer for its chunk list
    - Request missing chunks, **rarest first**
- **Sending chunks: tit-for-tat**
    - Send to the **top 4** peers currently sending at the highest rate
    - Others are **choked**
    - Re-evaluate top 4 every 10 secs
    - Every 30 secs, randomly pick another peer: **optimistically unchoke**
        - New peer may join the top 4
    - Higher upload rate = better trading partners = faster download

### 2.6 Video Streaming and CDNs

#### 2.6.1 Context

- Netflix, YouTube, Amazon Prime = ~80% of residential ISP traffic (2020)
- Challenges
    - **Scale**: reach ~1B users
        - _Single mega-server won’t work: single point of failure, congestion point, long path to distant clients, many copies sent over the same link_
    - **Heterogeneity**: wired vs mobile, bandwidth rich vs poor
- Solution: distributed, application-level infrastructure

#### 2.6.2 Multimedia: video

- **Video** is a sequence of images shown at a constant rate (ex. 24 images/sec)
- **Digital image** is an array of pixels, each represented by bits
- **Coding** uses redundancy to cut bits
    - **Spatial** (within an image): send colour value + number of repeats instead of N identical values
    - **Temporal** (image to image): send only differences from the previous frame
- **CBR**: constant bit rate, encoding rate fixed
- **VBR**: variable bit rate, changes with amount of spatial/temporal coding
- Examples
    - MPEG 1 (CD-ROM): 1.5 Mbps
    - MPEG 2 (DVD): 3 to 6 Mbps
    - MPEG 4 (often used on Internet): 64 Kbps to 12 Mbps

#### 2.6.3 Streaming stored video

- Simple scenario: video server (stored video) to client over the Internet
- Main challenges
    - Server-to-client bandwidth varies with congestion
    - Packet loss and delay delay playout or hurt quality
- Streaming: client plays the early part while the server is still sending the later part
- **Continuous playout constraint**
    - Playback must match original timing
    - Network delays are variable (**jitter**), so need a **client-side buffer**
- Other challenges
    - Interactivity (pause, fast-forward, rewind, jump)
    - Lost packets get retransmitted
- **Playout buffering**: client-side buffer and **playout delay** compensate for network delay and jitter

#### 2.6.4 DASH

- **Dynamic, Adaptive Streaming over HTTP**
- Server
    1. Divides video into multiple **chunks**
    2. Each chunk encoded at multiple rates, stored in different files
    3. Files replicated across CDN nodes
    4. **Manifest file** gives URLs for the different chunks
- Client (“intelligence” lives here)
    - Periodically estimates server-to-client bandwidth
    - Consults the manifest, requests one chunk at a time
    - Picks the max coding rate sustainable at the current bandwidth
    - Decides
        1. **When** to request (avoid buffer starvation or overflow)
        2. **What** encoding rate (higher when more bandwidth)
        3. **Where** to request from (a close server or one with high available bandwidth)
- **Streaming video = encoding + DASH + playout buffering**

#### 2.6.5 Content distribution networks (CDNs)

- Challenge: stream content (millions of videos) to hundreds of thousands of simultaneous users
- Option 1: single mega-server _doesn’t scale_
- Option 2: store/serve multiple copies at multiple geographically distributed sites (CDN)
    - **Enter deep**: push servers deep into many access networks, close to users
        - Ex. Akamai: 240,000 servers in 120+ countries (2015)
    - **Bring home**: smaller number (10’s) of larger clusters in POPs near (not within) access networks
        - Ex. Limelight

#### 2.6.6 Case study: Netflix

- Stores copies of content (ex. Mad Men) at its worldwide **OpenConnect** CDN nodes
- Flow
    
    1. Bob manages his Netflix account (registration and accounting servers in the **Amazon cloud**)
    2. Bob browses videos
    3. Subscriber requests content, service provider returns **manifest file**
    4. Client contacts a DASH server, streaming begins
    
    - Multiple versions of each video uploaded to CDN servers
- Using the manifest, client gets content at the highest supportable rate
    - May switch rate or copy if the path is congested
- **OTT** (“over the top”) challenges when coping with a congested Internet
    - Which CDN node to retrieve from?
    - Viewer behaviour during congestion?
    - What content to place in which CDN node?

#### 2.6.7 CDN content access (DNS in action)

- Ex. netcinema.com video stored in KingCDN
    1. Bob gets the video URL from the netcinema.com web page
    2. Bob’s local DNS resolves it, query goes to netcinema’s authoritative DNS
    3. netcinema’s DNS returns a **CNAME** pointing at KingCDN.com
    4. Bob’s local DNS asks KingCDN’s authoritative DNS, gets the IP of a CDN server
    5. Bob requests the video from that server, streamed via HTTP

### 2.7 Socket Programming

- Goal: build client/server apps that communicate using sockets
- Two socket types for two transport services
    - **UDP**: unreliable datagram
    - **TCP**: reliable, byte stream-oriented
- Example app
    1. Client reads a line from keyboard, sends to server
    2. Server converts characters to uppercase
    3. Server sends the modified data back
    4. Client displays the line

#### 2.7.1 UDP sockets

- **No connection**, no handshaking
- Sender explicitly attaches destination IP and port to _each_ packet
- Receiver extracts sender’s IP and port from the received packet
- Data may be lost or arrive out of order
- App sees unreliable transfer of groups of bytes (**datagrams**)
- Client steps
    1. Create socket: `socket(AF_INET, SOCK_DGRAM)`
    2. Get keyboard input
    3. `sendto(message, (serverName, serverPort))`
    4. `recvfrom(2048)` for reply
    5. Print, close socket
- Server steps (port 12000)
    1. Create UDP socket, `bind(('', serverPort))`
    2. Loop forever
    3. `recvfrom(2048)` gives message _and_ client address
    4. `.upper()`
    5. `sendto` reply to that client address

#### 2.7.2 TCP sockets

- Client must contact server
    - Server process must already be running
    - Server must have created a socket (door) that welcomes the client
- Client creates TCP socket with server IP and port, then **connects**
    - Client TCP establishes the connection to server TCP
- Server TCP creates a **new socket** for each contacting client
    - Lets the server talk to multiple clients
    - Source port numbers distinguish clients (Ch. 3)
- TCP gives reliable, in-order **byte stream** (“pipe”)
- Client steps
    
    1. `socket(AF_INET, SOCK_STREAM)`
    2. `connect((serverName, serverPort))`
    3. `send(sentence.encode())`, `recv(1024)`
    4. Close
    
    - _No need to attach server name and port to each message_
- Server steps
    
    1. Create **welcoming socket**, `bind`, `listen(1)`
    2. Loop forever
    3. `accept()` blocks until a request arrives, returns a **new connectionSocket**
    4. `recv(1024)`, `.upper()`, `send`
    5. Close connectionSocket (_not_ the welcoming socket)
    
    - `recv` reads bytes but not the address, unlike UDP

### 2.8 Chapter Summary

- Application architectures: client-server, P2P
- Service requirements: reliability, bandwidth, delay
- Transport service model
    - TCP: connection-oriented, reliable
    - UDP: unreliable, datagrams
- Specific protocols: HTTP, SMTP, IMAP, DNS, BitTorrent
- Video streaming, CDNs
- Socket programming: TCP, UDP sockets
- Typical request/reply exchange
    - Client requests info or service
    - Server responds with data and status code
- Message formats
    - **Headers**: fields giving info about the data
    - **Data**: payload being communicated
- Important themes
    - Centralized vs decentralized
    - Stateless vs stateful
    - Scalability
    - Reliable vs unreliable message transfer
    - “Complexity at network edge”