## Synchronization
- May be via a clock signal on a control line or via control bit/s included in data stream.
- Error checking is usually done with a parity bit.
- We might have:
```
data block = 
	1-2 Start bits
	Data bits
	(Parity) Check bits
	1-2 Stop bits
end
```
- This requires an initial negotiation, senders and receivers must agree on:
	- Transmission speed
	- Full or half-duplex
	- Number of start bits
	- Number of data bits
	- Number and meaning of check bits (parity)
	- Number of stop bits.
- Then, send DTR and DTS
	- Sender encodes data
	- Transmit/receive
	- Receiver decodes data
		- Check for errors
	- Either sends DTR or resends data (bad)
		- If there are too many errors, they must agree on a new handshake.
		- Usually this just means slower data transmission.
	- Eventually both agree, and transmission finishes.
- Lots of overhead, so it is crucial to distinguish:
	- Latency - time to send/receive 1 bit (≤9ms for some devices)
	- Throughput - bits/unit time Mb/s or MB/s which is much slower than latency.
## Multiplexing
- Can be used in parallel connections as a compromise between having one line/pin for each bit (fastest transmission) and reducing connector size but with less throughput.
	- Ex. Send a 64-bit transmission in 4x16 bit ones.
	- In hardware so it is transparent to software.
- Another form of MUX:
	- Use one interface to control multiple devices
		- Besides data lines, there are control bits to select a device
	- Prom a processor point of view,
		- Each interface controller presents a programming interface to the CPU which sends it instructions to execute locally.
		- It will likely use its own controller, perhaps an older CPU
## Buses
