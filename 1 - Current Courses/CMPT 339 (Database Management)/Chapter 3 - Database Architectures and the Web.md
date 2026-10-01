#incomplete 
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
![](z.%20Images/Pasted%20image%2020260924150548.png)
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
![](z.%20Images/Pasted%20image%2020260924150722.png)
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
![](z.%20Images/Pasted%20image%2020260924151818.png)
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
		- Services adhere to a comms contact defining the information exchange
	- Abstraction
		- All but necessary services logic is hidden from the outside world
	- Composability
		- Services may compose to others at various levels of granularity
	- Autonomy
		- Services have control over the logic they encapsulate
		- Not dependent on other services
	- Stateless
		- Services should not manage state information
	- Discoverability
		- Services are outwardly descriptive, so they cna be found via discovery
## Microservices Architecture
- This is the modern evolution of the SOA principles
	- Each service is a small, independently deployable, and owns its own DB
- Microservices are containerized (docker) and orchestrated (Kubernetes) for auto deployment/scaling
# Distributed DBMSs
- Distributed DB (DDB)
	- A logically interrelated collection of shared data, distributed physically over a computer network
- Distributed DBMS (DDBMS)
	- Software system permitting the management of the DDB (invisible to users)
	- A distributed DBMS reflects many companies org structure that is decentralized and distributed
- Accessed via apps
- Each site is capable of independently processing user requests
- Each fragment of the DDBMS is stored on one or more replica computers, each under the control of a separate DBMS
# NoSQL
- **NoSQL** stands for *not only SQL*
- A family of DB systems for storing and retrieving data without requiring the traditional relational-table model
- There are many types of NoSQL DBs:
- **Document Databases**
	- Store JSON/BSON documents, flexible schema, nested data
	- MongoDB, CouchDB, or Google Firestore
	- Content management, product catalogues, user profiles, etc.
- **Key-Value Databases**
	- Simple Key --> value pairs; very fast read/write
	- Redis, Amazon DynamoDB, Memcached
	- Caching, session storage, real-time leaderboards, shopping carts
- **Column-Family DBs**
	- Data organized into column families, optimized for write
	- Apache Cassandra, Apache HBase
	- IoT Data, time-series, write-heavy workloads, analytics at scale
- **Graph DBs**
	- Data as nodes and edges, optimized for relationship queries
	- Neo4j, Amazon Neptune
	- Social Networks, fraud detection, knowledge graphs, recommendation engines
- NoSQL emerged for a number of purposes:
	- Web-scale applications like Google or Amazon that had outgrown the scalability of relational DBs
	- Need for horizontal scaling
		- Share data across thousands of servers (**sharding**)
	- A more flexible schema, since not all data fits neatly in tables
	- Allows for operation even during server failures
- Review why to use NoSQL:
	- Flexible data structures
	- Very large datasets
	- High-throughput applications
	- Rapidly changing schemas
## ACID
- ACID is a set of four properties that ensure database transactions are processed reliably and correctly
- **Atomicity** - All operations happen, or none of them do
- **Consistency** - A transaction must take the database from one valid state to another.
- **Isolation** - Concurrent transaction shouldn't interfere with one another.
- **Durability** - Once a transaction is successfully committed, its changes should survive a crash.
## NewSQL
- These are distributed relational databases
- NewSQL systems provide the horizontal scalability or NoSQL while preserving full SQL and ACID guarantees
- Traditional RDBMS does not scale horiz.
	- NoSQL sacrifices ACID, so NewSQL bridges the gap
- Examples:
	- Google Spanner, CockroachDB, YugabyteDB, PlanetScale
	- These are the DBs powering the largest web-scale applications that need relational data
## Data Warehousing
- This allows an organization to turn its data archives into a source of knowledge
- **Data Warehousing** is a consolidated view of corporate data, drawn from disparate operational data sources, which serve to support decision making.
- Four key properties:
	1. **Subject Oriented**
		- Organized around major subjects (customers, sales) rather than application areas (invoicing, sock control)
	2. **Integrated**
		- Data from different systems is standardized into a unified view
	3. **Time-Variant**
		- Data is accurate at a specific point in time, and historical data is preserved
	4. **Non-Volatile**
		- Data is not updated in real time, but gets refreshed on a schedule
- **OLAP** (Online Analytical Processing)
	- The query style of data warehouses
## Data Lake
- A data lake stores raw data in its native format at massive scale
- Schema on Read: Structure applies when data is queried, not when it's stored
- **Data Warehouse vs. Lake**
	- **Warehouse** is structured, processed data, schema on write, expensive to change, fast SQL queries
	- **Lake** hosts raw data in native format, schema on read, cheap storage, flexible
- Data Swamp - a lake can turn into this without governance and a lack of metadata/quality control
## The Lakehouse Paradigm
- This combines the low-cost storage of a data lake with the data management and ACID guarantees of a data warehouse
- Open table formats add transaction support and schema enforcement to raw object storage
- Platforms like Databricks Lakehouse Platform, Snowflake, BigQuery
## Cloud Computing
- The use of multiple servers over a digital network, as if they were one computer.
- There are several key characteristics
	- On-demand self service
	- Broad network access
	- Resource pooling
	- Repaid elasticity (capacity scaling)
	- Measured service (usage is metered)
- 3 Service models:
	1. **Software as a Service (SaaS)**
		- Software/data hosted in the cloud
		- Accessed via browser, provider manages everything
		- Gmail, MS365, Salesforce, etc.
	2. **Platform as a Service (PaaS)**
		- Platform to build and deploy apps
		- Provider manages infrasatructure
		- Google App Engine, Azure App Service, Heroku
	3. **Infrastructure as a Service (IaaS)**
		- Raw compute, storage, and networking on demand
		- User manages everything from the OS and onward
		- Amazon EC2, Azure VMs, Google Compute Engine
## Serverless Computing
- A cloud execution model where the provider automatically provisions, scales, and manages infrastructure
- You deploy code, rather than servers
	- The servers exist, you just don't manage them
- **Functions as a Service (FaaS)**
	- Event-driven code execution, billed per millisecond
	- Deploy individual functions to the cloud.
	- AWS Lambda, Azure Functions, Google Cloud Functions
- **Serverless DBs**
	- Scale storage and compute independently, costs drop to $0 when idle
	- Ex. AWS Aurora Serverless - pauses when not in use, scales up to whatever you need
## Benefits of Cloud Computing
- Cost reduction
- Scalability
- Improved security
	- Providers invest in security at a scale no org can match
- Reliability
- Access to new technologies
- Faster development
- Global Reach
- Flexible working (from anywhere with internet)
## Costs of Cloud Computing
- Network dependency
- System dependency
- Vendor lock-in
	- Proprietary services make migration hard
- Cloud provider risk
	- Provider could become insolvent, change pricing, etc.
- Lack of control
- Data residency and compliance
- Lack of information on processing transparency
## Cloud-based DB Solutions
- As a type of SaaS, cloud-based DB solutions fall into two basic categories.
	1. Data as a Service (DaaS)
		- Provides data itself as a service via APIs
	2. Database as a Service (DBaaS)
		- Provides a fully managed DB
	- Key difference: DaaS gives you access to some else's data, where DBaaS gives you your own managed DB
## DaaS
- Enables data definition in the cloud and subsequent querying
- Doesn't implement a typical DBMS interface
	- Data access via APIs
- Enables orgs to offer valuable data access to others
- Examples:
	- Snowflake Data Marketplace - Share and monetize live data products
	- AWS Data Exchange - subscribe to 3rd party datasets
	- Databricks Delta Sharing - Share data live across orgs
	- Bloomberg - financial market data as a service
## DBaaS
- Offers full Db functionality to app devs
- Provider manages provisioning, scaling, backups, etc.
- Spares the dev from ongoing DB admin tasks
- Ex.
	- AWS RDS, Azure SQL DB, Firestore, MongoDB Atlas
- Customer-based provisioning and management using on-demand, self service mech
- There are several architectural options of DBaaS:
	- Separate servers
		- High isolation, dedicated per server tenant
		- Best for large, performance sensitive tenants
	- Shared server, separate DB server processes
		- Common virtualization, resources subdivided by tenant
	- Shared DBMS server, separate DBs
		- Single process shared,



















![](Pasted%20image%2020260929181339.png)