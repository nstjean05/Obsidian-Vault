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
- **UDP**: User Datagram Protocol
	- No-frills, bare bones, internet transport protocol
	- Best effort service, and UDP segments may be lost or delivered out of order
	- **Connectionless**:
		- No handshaking between UDP sender and receiver
		- Each UDP segment handled independently of others
- Given how simple it is, why does it exist?
	- No connection establishment delay
	- Simple, no connection state
	- Small header size
	- No congestion control
		- UDP can blast away as fast as desired
		- Can function in the face of congestion
- Usage of UDP in:
	- Streaming multimedia apps
	- DNS
	- SNMP
	- HTTP/3
	- If reliable transfer is needed over UDP, (HTTP/3)
		- Add needed reliability at application layer
		- Add congestion control at application layer
- UDP is outlined in RFC 768, 1980
#### UDP Transport Layer Actions
- **Sender Actions**
	- Is passed an application-layer message
	- Determines UDP segment header fields values
	- Creates UDP segment
	- Passes segment to IP
		- IP then forwards the datagram to the receiving IP host
- **Receiver Actions**
	- Receives segment from IP
	- Checks UDP checksum header value
	- Extracts application-layer message
	- Demultiplexes message up to applications via socket
#### UDP Segment Header
- Only 4 fields + payload
- Length --> Length of payload
![284](Pasted%20image%2020261027154117.png)
#### Internet Checksum Field
- Goal is to detect errors (flipped bits) in transmitted segment
![275](Pasted%20image%2020261027154241.png)
- **Sender**
	- Treat contents of UDP segment as a sequence of 16-bit integers
	- Checksum: Addition of segment content
	- Checksum value put into UDP checksum field
- **Receiver**
	- Compute checksum of received segment
	- Check if computer checksum equals checksum field value
		- ≠ --> Error detected
		- = -> No error detected
	- In some cases this is imperfect, as different combinations of values can have the same sum
	- There are stronger methods of bit detection, but this is a good starting point
# 3.4 - Principles of Reliable Data Transfer
- We want to send via a reliable channel from sender to receiver
- Consider only unidirectional data transfer
	- Sender and receiver only know about what the other is doing by what the other tells them
#### RDT 1.0. - Reliable transfer, Reliable Channel
- Underlying channel perfectly reliable
	- No bit errors
	- No loss of packets
- *Separate* FSMs (finite state machines) for sender and receiver
	- Sender sends data into underlying channel
	- Receiver reads data from an underlying channel
- Steps transfer:
	1. Sender gets data and bundles it in a packet
	2. Sends the packet into the reliable channel
	3. Receiver, waiting, receives the packet
	4. Extracts the packet data
	5. Delivers the data to the machine
#### RDT 2.0 - Channel With Bit Errors
- Underlying channel may flip bits in packet
	- How do we recover from errors?
- Acknowledgements (yes) and negative acknowledgements (no) are used in human communications
	- ACKs - Receiver tells sender that pkt received OK
	- NAKs - Receiver explicitly tells sender that pkt had errors
		- Sender then retransmits pkt on receipt of NAK
- Stop and wait method: sender sends a packet, then waits for a response
![466](Pasted%20image%2020261027161210.png)
- One major flaw: What happens when ACK/NAK is corrupted
	- Can't just retransmit, or we get duplicates
- Handling duplicates
	- Sender retransmits current pkt if ACK/NAK corrupted
	- Sender adds a sequence number to each packet
	- Receiver discards the duplicate packer
		- Don't deliver it up to the application layer
#### RDT 2.1 - Sender, handling garbled ACK/NAKs
- Stop and wait protocol
	- 1 bit sequence number
	- Four states:
		- First two are for sending when sequence number is 0
		- Second two for sequence number 1
![450](Pasted%20image%2020261027171237.png)
- Either way, the corruption is caught and resolved.
- **Sender**
	- Sequence number added to packet
	- Two sequence numbers will suffice
	- Must check if received ACK/NAK corrupted
	- Twice as many states
		- They must remember whether expected pkt is 1 or 0
- **Receiver**
	- Must check if received packet is a duplicate
		- State indicates whether 0 or 1 is expected pkt sequence number
	- Note: Receiver cannot know if its lack ACK/NAk received OK at sender
#### RDT 3 - Channels with Errors and Loss
- New Channel Assumption
	- Underlying channel can also *lose* packets
		- Checksum, sequence numbers, ACKs, retransmission will be of help, but insufficient
- Approach: Sender waits a reasonable amount of time for ACK
	- Retransmits if no ACK is received in time
	- If pkt or ACK just delayed, not lost:
		- Retransmission will be a duplicate, but sequence numbers handle this
		- Receiver must specify the sequence number of packet being ACKed
	- Use countdown timer to interrupt after a reasonable amount of time is passed
![413](Pasted%20image%2020261027172714.png)
- **Example**
	1. Sender send pkt0 to Receiver
	2. Receiver receives pkt0
	3. Receiver sends ack0
	4. Sender receives ack0
	5. Sender sends pkt1
		- Repeat (no loss)
	6. Packet 1 is lost
	7. Sender waits until timeout
	8. Sender resend pkt1
	9. Receiver receives pkt1, sends ack1
	10. Ack1 is lost
	11. Sender waits until timeout
	12. Sender resend pkt1
	13. Receiver receives pkt1, detects duplicate, sends ack1
	14. Receiver receives ack1
	15. Sender sends pkt0
	16. Receiver receives pkt0, Sender times out prematurely, Receiver sends ack0
	17. Sender sends pkt0 again, ignores the first ack0
	18. Receiver receives pkt0, detects duplicate, sends ack0
	19. Sender receives ack0
- Remember to alternate between 0 and 1
- The performance metric we are interested in is utilization
	- Fraction of time sender is busy sending
- Example: 1Gbps link, 15 ms prop delay, 8000 bit packet
	- Time to transmit packet into channel:
		- D_trans = L/R = 8000 bits/ 10$^9$ bits/sec = 8 microseconds
#### Go Back N: Sender
- Sender: window of up to N, consecutive transmitted but unACKed pkts
	- K-bit sequence number in pkt header
- Cumulative ACK(n): ACKs all packets up to, and including seq num n
	- On receiving ACK(n): move window forward and begin at n+1
- Timer for oldest in-flight packet
- Timeout(n): Retransmit packet n and all higher seq num packets in window
#### Go Back N: Receiver
- ACK only: Always send ACK for correctly-received packet so far, with highest in-order seq num
	- May generate duplicate ACKs
	- Need only remember rcv_base
- On receipt of out of order packet,
	- Can discard (don't buffer) or buffer - an implementation decision
	- re-ACK pkt with highest in-order seq num
![509](Pasted%20image%2020261027174702.png)
#### Selective Repeat
- Receiver individually ACKs all correctly received packets
	- Buffers packets, as needed, for eventual in-order delivery to upper layer
- Sender times out or retransmits individually for unACKed packets
	- Sender maintains time for each unACKed packet
![508](Pasted%20image%2020261027174930.png)
- **Sender**
	- Data from above:
		- If next available seq num in window, send packetg
	- Timeout(n):
		- Resend packet n, restart timer
	- ACK(n) in (sendbase, sendbase + N)
		- Mark packet n as received
		- If n smallest unACKed packet, advance window base to next unACKed seq num
- **Receiver**
	- Packet n in (rcvbase, rcvbase + N -1)
		- Send ACK(n)
		- Out of order: buffer
		- In order: deliver, advance window to next not yet received packet
	- Packet n in (rcvbase - N, rcvbase - 1)
		- ACK(n)
	- Otherwise, ignore
![490](Pasted%20image%2020261027175500.png)
# 3.5 - Connection-Oriented Transport (TCP)
#### TCP Overview
- Point to point
	- One sender, one receiver
- Reliable, in-order byte stream
	- no message boundaries
- Full duplex data
	- Bi directional data flow in the same connection
	- MSS: Maximum segment size
- Cumulative ACks
- Pipelining
	- TCP Congestion and flow control set window size
- Connection oriented
	- Handshaking initializes sender, receiver state before data exchange
- Flow controlled
	- Sender will not overwhelm receiver
![555](Pasted%20image%2020261027190354.png)
#### TCP Sequence Numbers, ACKs
- Sequence Numbers
	- Byte stream 'number' of first byte in segment's data
- Acknowledgements
	- Sequence number of next byte expected from the other side
	- Cumulative ACK
- TCP spec doesn't decide how to handle out of order packets
![](Pasted%20image%2020261027190659.png)
- Sequence numbers go up alternating
	- ACK goes up on each send from A --> B
	- Seq goes up on each send B --> A
#### TCP Round Trip Time and Timeout
- How to set TCP timeout value?
	- Longer than RTT, but RTT varies
	- Too short: premature timeout, unnecessary retransmission
	- Too long: Slow reaction to segment loss
- How to estimate RTT?
	- SampleRTTs
		- Measured time from segment transmission until ACK receipt
			- Ignore retransmissions
		- Will vary, want estimated RTT to be smoother
			- Average several recent measurements, not just current SampleRTT
- Timeout interval
	- EstimatedRTT plus 'safety margin'
	- Large variation in EstimatedRTT --> want a safer margin
	- TimeoutInterval = Estimated RTT + 4•DevRTT
- DevRTT EWMA of SampleRTT deviation from EstimatedRTT
	- DevRTT = (1-ß)•DevRTT + ß • |SampleRTT - EstimatedRTT|
	- Usually, ß = 0.25
#### TCP Sender
- Event: Data received
	- Create segment with seq number
	- Sequence number is a byte stream number of first data byte in segment
	- Start timer if not alr running
		- Think of timer as for oldest unACKed segment
		- Expiration interval: TimeOutInterval'
- Event: Timeout
	- Retransmit segment that caused timeout
	- Restart timer
- Event: ACK received
	- If ACK acknowledges previously unACKed segments
		- Update what is know to be ACKed
		- Start timer if there are still unACKed segments
#### TCP Receiver: ACK Generation

|**Event at receiver**|**TCP receiver action**|
|---|---|
|arrival of in-order segment with expected seq #. All data up to expected seq # already ACKed|delayed ACK. Wait up to 500ms for next segment. If no next segment, send ACK|
|arrival of in-order segment with expected seq #. One other segment has ACK pending|immediately send single cumulative ACK, ACKing both in-order segments|
|arrival of out-of-order segment higher-than-expect seq. #. Gap detected|immediately send _duplicate ACK_, indicating seq. # of next expected byte|
|arrival of segment that partially or completely fills gap|immediate send ACK, provided that segment starts at lower end of gap|
1. Lost ACK
	- Host A → Host B: `Seq=92, 8 bytes of data`
	- ACK (`ACK=100`) is **lost**
	- No confirmation → A's **timeout** fires
	- A **retransmits** `Seq=92` → B sends `ACK=100` again
	- Note: B discards duplicate data, resends ACK
2. Premature Timeout
	- A sends `Seq=92` (8 bytes), then `Seq=100` (20 bytes) — both received
	- B ACKs both, but **timeout fires before ACKs arrive**
	- A retransmits `Seq=92` → B **re-ACKs with cumulative `ACK=120`**
	- Key points:
	    - SendBase advances: 92 → 100 → 120
	    - Duplicate segments are **discarded**, but **re-ACKed**
	    - Retransmission is wasteful but safe
3. Cumulative ACK Rescues Lost ACK
	- A sends `Seq=92`, `Seq=100`; B's `ACK=100` is lost (✗)
	- B receives `Seq=120, 15 bytes` next
	- B replies `ACK=120` — **cumulative ACK covers the lost ACK**
	- No retransmission needed
- **TCP Fast Retransmit**
	- If sender receives 3 ACKs for same data, resend unACKed segment with smallest sequence number
		- Likely that unACKed segment was lost, so don't wait for a timeout
![249](Pasted%20image%2020261027192241.png)
#### TCP Flow Control
- Sometimes network layer data is delivered faster than application layer can remove data from socket buffers
	- Ex. Trying to drink from a fire hose
- TCP receiver advertises free buffer space in *rwnd* field in TCP header
	- RcvBuffer size set via socket options (usually 4096 bytes)
	- Many OSs autoadjust RcvBuffer
- Sender limits amount of unACKed ('in-flight') data to received rwnd
- Guarantees receive buffer will not overflow
#### TCP Connection Management
- Before exchanging data, sender/receiver 'handshake'
	- Agree to establish connection
	- Agree on connection parameters
- Will a 2-way handshake always work in a network?
	- variable delays
	- Retransmitted messages due to message loss
	- Message reordering
	- Can't 'see' the other side
#### 2-Way Handshake Scenarios
- Flawless scenario:
![345](Pasted%20image%2020261027193213.png)
- Server is left hanging open with an established connection, but the client has already completed its work and terminated
![277](Pasted%20image%2020261027193450.png)
- A connection has been re-established, and data retransmitted, but the connection is left open and duplicate data is accepted
![275](Pasted%20image%2020261027193548.png)
#### TCP 3-Way Handshake
![](Pasted%20image%2020261027193853.png)
- **Setup**
	- **Server:** creates socket → `bind()` → `listen()` → waits in **LISTEN** state, then `accept()`
	- **Client:** creates socket → calls `connect((serverName, serverPort))`
- *The 3 Steps*

|Step|Who|Message|Meaning|
|---|---|---|---|
|1|Client → Server|`SYNbit=1, Seq=x`|"I want to connect" — client picks random initial seq # x|
|2|Server → Client|`SYNbit=1, Seq=y; ACKbit=1, ACKnum=x+1`|"Agreed — and I'm alive too" — server picks its own seq # y, ACKs client's SYN|
|3|Client → Server|`ACKbit=1, ACKnum=y+1`|"Confirmed" — final ACK; **may also carry client-to-server data**|
- State Transitions
	- **Client:** `CLOSED` → **SYNSENT** (after sending SYN) → **ESTAB** (after receiving SYNACK)
	- **Server:** **LISTEN** → **SYN RCVD** (after receiving SYN) → **ESTAB** (after receiving ACK)
- Why It Works
	- Server learns client is **live** when it receives the SYNACK's ACK
	- Client learns server is **live** as soon as the SYNACK arrives
	- Both sides agree on **initial sequence numbers** (x, y), which sync byte ordering and detects old/duplicate segments
	- After step 3, both are in **ESTAB** and data can flow in both directions
#### Closing a TCP Connection
- Client, server each close their side of connection
	- Send TCP segment with FIN bit = 1
- Respond to received FIN with ACk
	- On receiving FIN, ACK can be combined with own FIN
- Simultaneous FIN exchanges can be handled
- This way, each can wait around a bit for the other, ensuring a graceful closing
# 3.6 Principles of Congestion Control
- Congestion
	- All about too many sources sending too much data too quickly for the network to handle
- Manifestations
	- Long delays - queuing in router buffers
	- Packet loss - Buffer overflow at routers
- Flow control is different - single sender and receiver
#### Simplest Example
- One router, infinite buffers
- Input, output link capacity: R
- Two Flows
- What happens as arrival rate approaches R/2?

![368](Pasted%20image%2020261027203329.png)
#### Scenario 2: Finite Buffer
- One router, finite buffers
- Sender retransmits lost, timed-out packets
	- Application layer input = application layer output ƛin = ƛout
	- Transport layer input includes retransmissions, ƛ'in ≥ ƛin
- Idealization
	- Packets can be lost due to full buffers
	- Sender know when packet has been dropped, only resending if packet is known to be lost
![494](Pasted%20image%2020261027203842.png)
![249](Pasted%20image%2020261027203852.png)
#### Scenario 3: Realistic
- Realistic scenario: Un-needed duplicates
- Packets can be lost, dropped at router due to full buffers
	- Requires retransmission
- But sender times can time out prematurely, sending two copies, both of which are delivered.
![417](Pasted%20image%2020261027204043.png)
- Costs of congestions:
	- More work (retransmission) for given receiver throughput
	- Unneeded retransmissions: link carries multiple copies of a packet
		- Decreasing maximum achievable throughput
#### Scenario 4
- Four senders
- Multi-hop paths
- Timeout/retransmission
- If a packet makes it through one router, but fails at the second, then the host must resend it from the beginning
- As one host increases its packets, all arriving packets from host2 are dropped, leading to host2's throughput going to 0
	- If the host is farther away from the link, it has less priority (as host2 did)
- Another cost of congestion
	- When packet is dropped, any upstream transmission capacity and buffering used for that packet was wasted
#### Insights
- Throughput can never exceed capacity
- Delay increases as capacity is approached
- Loss/retransmission decreases effective throughput
- Un-needed duplicates further decrease effective throughput
- Upstream transmission capacity and buffering is wasted for packets lost downstream
	- Going to 0 --> congestion collapse
# 3.7 - TCP Congestion Control
- Approach: Senders can increase sending rate until packet loss occurs, then decrease sending rate on a loss event
![362](Pasted%20image%2020261027204956.png)
- AIMD - Additive increase, multiplicative decrease
	- Algorithm dictating how much to cut send rate
	- Goes up, then drops by a factor of 2
- Multiplicative Decrease
	- Sending rate is cut in half on loss detected by triple duplicate ACK
	- Sending rate is cut to 1 MSS (max segment size) when loss detected by timeout (TCP Tahoe)
- Why AIMD?
	- Concern of a multiplicative increase is that it grows too fast
	- Optimize congested flow rates network ride
	- Stability
#### Control Details
- TCP Sender limits `transmission LastByteSent - LastByteAcjed ≤ cwnd`
- cwnd is dynamically adjusted in response to observed network congestion
- TCP Sending behaviour:
	- Roughly, send cwnd bytes, wait for RTT for ACKs, then send more bytes
	- TCP rate ~= cwnd/RTT bytes/sec
#### TCP Slow Start
- When connection begins, increase rate exponentially until first loss event
	- Initially cwnd = 1 MSS
	- Double cwnd = cwnd every RTT
	- Done by incrementing cwnd for every ACK received
- Summary: Initial rate is slow, but ramps up exponentially fast
![226](Pasted%20image%2020261027205637.png)
#### From Slow Start to Congestion Avoidance
- The exponential increase should switch to linear when cwnd gets to 1/2 of its value before timeout
- Implementation:
	- Variable ssthresh
	- On loss event, ssthresh is set to 1/2 just before loss event
#### TCP Cubic
- W_max - Sending rate at which congestion loss was detected
- Congestion state of bottleneck link probably hasn't changed much 
- After cutting rate in half on loss, ramp quickly back up to almost the loss, then increase very slowly
- K: point in time when TCP window size will reach W_max
	- K itself is tuneable
- Increase W as a function of the cube of the distance between current time and K
	- Larger increases when further away from K
	- Smaller increases when nearer K
#### TCP and the Congested Bottleneck Link
- TCP (classic, CUBIC) increase TCP's sending rate until packet loss occurs at some router's output: the bottleneck link
- Understanding congestions: Useful to focus on congested bottleneck link
- Insight: Increasing TCP sending rate will not increase end-end throughout with congested bottleneck
	- Increasing TCP sending rate will increase measured RTT
	- Goal: Keep the end-end pipe full, but not fuller
- **Delay-based approach**
	- RTT_min --> Minimum observed RTT (uncongested path)
	- Uncongested throughput with congestion window cwnd/RTT_min
- Throughput = (bytes sent in last RTT interval)/(RTT_measured)
- If throughput is very close to uncongested throughput, increase cwnd linearly
- If throughput is far below uncongested throughput, decrease cwnd linearly
- **cwnd** = Congestion window
	- The amount of data (in bytes) that a TCP sender may have in flight (unACKed) at once
- Congestion control without inducing loss
- Maximize throughput while keeping delay low
- Several deployed TCPs take a delay-based approach
#### Explicit Congestion Notification
- TCP deployments often implement *network assisted* congestion control
	- Two bits in IP header marked by network router to indicate congestion
	- Congestion indication carried to destination
	- Destination sets ECE bit on ACK segment to notify sender of congestion
	- Involves both IP and TCP
#### TCP Fairness
- If K TCP sessions share same bottleneck link of bandwidth R, each should have an average rate of R/K
![384](Pasted%20image%2020261027211035.png)
- TCP is fair under ideal assumptions
	- Same RTT
	- Fixed number of sessions only in congestion avoidance
- **Fairness and UDP**
	- Multimedia apps often don't use TCP
		- Don't want rate throttled by congestion control
	- Instead use UDP
		- Send audio/video at constant rate, toler








