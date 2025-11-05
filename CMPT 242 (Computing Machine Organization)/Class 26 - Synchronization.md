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
