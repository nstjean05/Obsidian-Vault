- The DD interaction is modulated by:
	- A request queue (in the CSR space) where the API deposits requests and the back end fetches them.
		- Control Status Register
		- Application Programming Interface
	- One or more data buffers for temporary storage
		- Waiting on the appropriate commands.
- **Note**: Because the back end generates interrupts on task completion, it enables itself to be re-invoked to service the next request
	- The instruction flow could be modified
	- If request queue empty, clean interrupt status return
- **Note:** A device driver CSR has an interrupt bit that can be set by calling the API to force an interrupt.
	- If it is idle, if already working nothing happens.
	- Effect of doing this: The APU need not ask if the device is busy - just set the bit and drop in a request.
- Queued Input
	- Can be handled simply with input events and dot buffered by the backend - waiting for the application to pull data via requests.
## Routine
- Init
	- Initialize input space
	- Set interrupt bit
- Front end read
	- If input queue is empty, suspend application on wait queue, then return to application
- Back End
	- If queue/buffer not full queue another input operation
	- If app waiting , signal it to start
	- When done, interrupt to notify everyone.
## Bidirectional Strategies
- Treat as:
1. Two independent devices each with its own CSRs and interface parallel
2. As a single device with one queue and buffer but with a read.write status but in CSR
	- Must be able to handle a read request on queued output data
- **Note:** Polling is synchronous (code looks for events)
	- Interrupts are asynchronous (events are just signals to request attention)
- Asynchronous events must have an exclusion mechanism