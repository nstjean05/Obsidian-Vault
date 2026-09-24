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
	- Less expensive hardware, since the client is 'thin'
	- Application maintenance is centralized, and business logic is in one place
	- Modularity between tiers
	- Easier load balancing, since business and DB functions are separated
	- Maps naturally onto the web environment
- N-Tier architectures:
	- 3-tier architecture can be expanded to n-tiers with additional tiers providing more flexibility and scalability
- Application servers
	- Hosts an API to expose business logic and processes for use by other applications
	- Handles: concurrency, network connection management, database connection pooling
		- Legacy DB support, clustering, load balancing, failover
- Modern equivalent: micro-services running on container orchestration programs (e.g. Kubernetes)
# Middleware
- Describes software that mediates with other software and allows for communication between separate apps in a heterogenous system
- Acts as the glue between platforms/languages/vendors
	- Software connecting components
- **Transaction Processing Monitor**
	- A program that controls data transfer between clients/servers to provide a consistent environment
		- Used in online transaction processing
	- Transaction routing - directs transactions to a specific DBMS
	- Managing distributed transactions
	- Load balancing
	- Funnelling - Pools connections so all users share a small set of DBMS connections
	- Increased reliability
![](Pasted%20image%2020260924151818.png)
# Web Services and Service-Oriented Architectures
- Web Services
	- A software designed to support interoperable machine-machine interaction over a network
	- No UI
	- A key technology for B2B integration
	- Shares business data/logic/processes
	- Developers can add a web service to a web page to offer users specific functionalities
		- Ex. Google Maps API, Stripe Payment, etc.
- There are many legacy web enterprise standards:
	- eXtensible Markup Language (XML)
		- Universal structured data format
	- Simple Object Access Protocol
		- XML-based messaging protocol
	- Web Services Description Language
		- XML protocol to describe and locate a web service
	- Universal Discovery, Description, and Integration
		- XML-based registry
	- RESTful Web Services
		- REST = Representational State Transfer
		- Dominant today
## RESTful Web Services
- REST is the dominant architectural style for web APIs today
- Resources are identified by URLs and manipulated using standard HTTP verbs
	- Ex. GET, POST, PUT, etc.
- Stateless - each request carries all the needed information
- Returns JSON or XML, and works over play HTTP
	- Ex. GitHub APU, Twitter APU, mobile app backends, etc.
## Graph QL
- A modern API query language
- Developed at Meta in 2015
- Allows for clients to request only the data they need
- REST has a limitation, as its fixed response shape risks over/under-fetching data
- GraphQL solves this by having a single endpoint, and the client specifies exactly which fields to return
- Fetch nested or related data in a single request, rather than multiple trips
- Ex. GitHub, Shopify, Twitter, etc.
- **Use ___ if:**
	- Rest for simple CRUD APIs, when caching is important, or public APIs
	- GraphQL for complex data relationships, mobile apps which are bandwidth-sensitive, and rapid UI iteration
# Server-Oriented Architectures (SOA)
- SOA is a business-centric software architecture for building applications that implement business processes, at granularity relevant to the user
- Many principles
	- Loose coupling
		- Services designed to interact on a loose basis
	- Reusability
		- Logic that can be reused and is designed as a separate service
	- Contract
		- 
	- Abstraction
	- Composability
	- Autonomy
	- Stateless
	- Discoverability
- 