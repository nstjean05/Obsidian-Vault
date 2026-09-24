# Multi-user DBMS Architectures
- **Teleprocessing**: Traditional architecture for multi-user systems
	- One computer with a single CPU and a few terminals
	- Put massive burden on the central computer
- Downsizing
	- 1980s onwards
	- Replacing expensive mainframe computers with cost-effective networks of personal computers
- M-U DBMS has file-server architecture
	- Processing gets distributed throughout the network
	- File-server is connected to several workstations
		- Like a shared Hard Disk Drive (HDD)
![](Pasted%20image%2020260924150548.png)
- Database resides on the file-server
	- Inflicts a large amount of network traffic
	- Full copy of DBMS is required on workstation
	- Concurrency, recovery, and integrity control are complex
	- Multiple DBMSs can access the same files
- These limitations incited the client-server model
# Client-Server Architecture
- Server holds both the DB and the DBMS
- Client manages the UI and runs apps
- Allows for:
	- Wider access to existing DBs
	- Increased performance
	- Possible reduction in hardware costs
	- Reduction in communication costs
	- Increased consistency
![](Pasted%20image%2020260924150722.png)
# Multi-user DBMS Architectures 2.0
- 3-tiered client-server architecture
	- Introduced around 1995
	- Problems of a 'fat' client and client-side admin overhead
	- By 1995, 3 layers were proposed, each potentially running on a different platform
- 3-Tiers:
	1. UI (Thin client; browser or light apps)
	2. Application Server (Business logic & data processing)
	3. DBMS (DB server)
- This design has many advantages:
	- Less expens