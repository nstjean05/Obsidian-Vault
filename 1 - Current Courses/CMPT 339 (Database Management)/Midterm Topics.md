# Data, Information, Knowledge, and Wisdom
- **Data**: Unprocessed measurements without context
- **Information**: Data, with context
	- Has been structured and organized
- **Knowledge**: Processed information, answering the *how*.
	- Ex. Knowing that 37° is the normal human temperature, and that your temp of 28.9° indicates a fever.
- **Wisdom**: Knowledge and judgement
	- Why has something happened, and what should we do next
# Definitions of Metadata, Database, DBMS, Warehouse, Informatics, Data Mining, etc.
- **Metadata**: Data about data, describing the structure and properties
- **DBMS**: Software layer between users/applications and the physical DB
- **Data Warehouse**: A central repo for reporting and analysis
	- Unifies all of an organizations cleaned data in one place
- **Data Lake**: A vast storage repo for holding all raw unprocessed data in its original formats
- **Data Mining**: Compute process to find patterns and models in large datasets
- **Informatics**: Study of how information is represented/processed/etc in a domain
# File-based approach (limitations)
- Pre-Relational DBMS
- Data stored in separate flat files, each managed directly by custom apps
1. Data became over-redundant and inconsistent
	- When one file updates, a related file elsewhere wasn't
2. Data is isolated across various apps and formats
3. The structure of the data file is hardcoded into how it interacts with the program
4. Rule cannot be enforced at the storage layer
	- Ex. a value (like GPA) must be in a certain range, but the app can't enforce that in storage
5. If programs crash mid operation, information is lost
6. Concurrency breaks down
7. Security and access control issues
	- Hard to separate access to data within a file
# DBMS advantages and disadvantages
- **Advantages**
1. Redundancy and consistency
	- Duplicate data can be eliminated and controlled, preventing conflicting updates
2. Data is independent, allowing apps to interact with logic rather than a storage layout
	- Storage can be changed without affecting code
3. Constraints can be enforced automatically at the DB level regardless of which app modifies the data
	- Primary/Foreign keys 
4. Concurrency
5. Backups and crash recovery
6. Role permissions and security
- **Disadvantages**
1. High cost of development
	- Ongoing license
2. Complex system
3. Performance overhead
4. Single point of failure
	- MS365 Outage
5. Migration costs
- When to avoid a DBMS:
	- Dataset is small, static, and used by one application
	- Real time, low latency constraints
	- Data is heavily unstructured
# DDL and DML
- **Data Definition Language**
	- DDL
	- Defines and modifies the DB schema/structural objects
	- Updates metadata
- **Data Manipulation Language**
	- DML
	- Retrieves, inserts, modifies the actual data rows inside tables
# Characteristics of views

# The components of DBMS environment
- **Hardware**
	- Physical equipment the system runs on
	- From 1 PC to a network of computers
- **Software**
	- DBMS, OS, and network software
	- Application programs using the DB
- **Data**
	- Org data, plus its description (schema)
	- Link connecting machine and human parts
- **Procedures**
	- Instructions and rules for DB design/use
- **People**
	- Covered next.
# Various roles (DA, DBA, Database Designer, Application Designer, End Users, etc.)
- **Data Admin**
	- DA
	- Manages data resource
	- Planning/standards/policies/design
- **DB Admin**
	- DBA
	- Physical side
	- Implementation/security/integrity/backups/perfomance
- **DB Designer**
	- Identify data and relationships/constraints
- **End Users**
	- Clients served by the whole system
- **Application Developers**
	- Write the programs that give end users functionality
# Edgar F. Codd and Peter Chen
- **Edgar Codd**
	- Inventor of the relational model
	- IBM Research lab, 1970s
- **Relational Model**
	- Data stored as relations (tables) of rows and columns
- Codd's paper led to SEQUEL and then SQL
- **Peter Chen**
	- Inventor of the entity-relationship model
	- 1976 npaper
- **ER Model**
	- Top-down approach to DB design
	- Identify entities/relationships, then add attributes/constraints
	- Basis for ER diagrams
# ANSI-SPARC Architecture
- Levels allowing users to see only the data they need, without worrying about how it is stored.
1. **External Level**
	- Describes the part of the DB relevant to a specific user group
	- Different views can show the same data differently
	- Many external views
2. **Conceptual Level**
	- Describes what data is stored, and the relationships among it
	- All entities, attributes, relationships, and constraints on data
	- Mapping and independence between external/internal levels
	- Only 1 conceptual schema per DB
3. **Internal Level**
	- Physical representation of the DB on the computer
	- Data structures and file organization
	- Concerned with storage space, record placement, data compression, and encryption
- This design allows for any of the layers to be changed, without disruption to the others
	- Logical and physical data independence
# Three-tier client–server architecture (middle tier, middleware)
- **Two-Tier**
	- Client holds the UI and business logic, while server supplies data services
	- Results in a fat client, with logic living on each machine, making updates challenging
- 3-tier splits an application into 3 layers, each running on its own machine
- **Tier 1**: Client
	- Handles the UI only
	- Usually a web browser or light app
- **Tier 2**: Middle
	- Business logic and data processing
	- This is the application server
	- Concurrency, network connection, DB connect, load balancing, etc
- **Tier 3:** DB Server
	- DBMS and DB itself
	- Only the application server talks to it, so the clients never connect to the DB directly
- **Advantages**
	- Cheaper hardware (clients are thin)
	- App logic in one place
	- Modularity
	- Load balancing
- **Middleware**
	- Software that mediates between other software and lets distinct apps communicate
	- The application server is itself a kind of middleware
- **Transaction Processing Monitor**
	- TP monitor
	- Type of middleware
	- Control data transfer between clients and servers to give a consistent environment
	- Online transactions are a common case
# Data independence (logical and physical)
- **Logical Independence**
	- External schema cannot affect logic of the conceptual schema
	- Adding or removing entities/attributes/relationships in conceptual shouldn't break user views
- **Physical Independence**
	- Physical changes should not affect the conceptual schema
	- Various file orgs or storage structures shouldn't require changes to higher levels
- Logical independence is generally hard to achieve in practice
	- Structural changes to the data can affect what users and programs need
# Different data models
- Data models integrate concepts for describing data
- Three parts of a data model:
	1. Structural: Rules for how the DB is built
	2. Manipulative: Types of operations allowed
	3. Integrity: Keep the data accurate
- **Object-Based Models**
	- Built from entities, attributes, and relationships
	- Ex. ER Model
- **Record-Based Models**
	- DB made of fixed-format records, with different types of fixed length
	- Three variants:
		1. Relational - based on relations, organized as tables
		2. Network - data stored as collections of records, relationships represented as sets
		3. Hierarchical - A tree, with each node having one parent
- **Physical Data Models**
	- Describes how data is stored in the computer
		- Record structures
		- Record orderings
		- Access paths
	- ANSI-SPARC internal level
# File-server vs. client-server architectures
- **File-Server**
	- Central DB on the file server, connected to several workstations
	- Similar to a shared hard drive
	- Distributed processing
	- A full copy of the DBMS on each workstation
	- When a station needs data, it sends for it from the file server
- **Client-Server**
	- Server holds the DBMS and the DB
	- Client manages the UI and runs apps
	- Client sends requests to the server, and is given only the results
- **Weaknesses**
	- File server leads to heavy network traffic and redundant DBMSs
- **Strengths**
	- Client server has increased performance and consistency
# Teleprocessing, web service, REST, SOA, microservices, NoSQL, NewSQL, transaction processing monitor
- **Teleprocessing**
	- Traditional architecture
	- One central computer with 1 CPU, and several dumb terminals
	- Terminals only send input and show output
	- Huge burden on central computer, bad scaling
- **Web Service**
	- Software system for machine to machine interaction over a network
	- No UI
	- Shares business logic and data
		- B2B integration
- **REST**
	- Representational State Transfer
	- Architecture for web APIs
	- Resources are identified by URIs and manipulated with HTTP verbs
- **SOA**
	- Service-Oriented Architecture
	- Business centric architecture for building apps from services
- **Microservices**
	- Modern evolution of SOA
	- Many small, independently deployable services
	- Each service owns its own DB and comms through light APIs
	- Ex. Docker/Kubernetes
- **NoSQL**
	- Not Only SQL
	- DBs that store and retrieve data without the traditional relational table model
	- Flexible data structures, very large datasets, high throughput
- **NewSQL**
	- Distributed relational DBs that give NoSQL's scalability while keeping full SQL and ACID transactions
- **Transaction Teleprocessing Monitor**
	- Middleware for online transaction processing
	- Provides a consistent environment for data transfer between client/server
- **ACID**
	- Atomicity
		- Transactions as a single unit
	- Consistency
		- A transaction moves the DB from one valid state to another
	- Isolation
		- Concurrent transaction execute without interfering with one another
	- Durability
		- Once a transaction is committed, its changes are permanent, and survive system restart/crash
# Distributed processing, distributed DBMS
- **Distributed Processing**
	- Processing is spread over a network of computers, while data is centralized in a DB
	- Communicate over a network
- **Distributed DB**
	- Logically interrelated collection of shared data, physically distributed over a computer network
- **Distributed DBMS**
	- The software system managing the DDB, and making the distribution transparent to users (they can't tell it's there)
	- Appears centralized
# Data warehousing, data lake, and lakehouse
- **Warehousing**
	- Consolidated view of an org's data for disparate sources
	- End-users have tools that let them do queries
	- Four properties:
		1. Subject oriented
			- Organized around major subjects (customers/sales)
			- Not around application areas (invoicing/stock control)
		2. Integrated
			- Data from many sources
		3. Time-variant
			- Data is accurate at a specific point, and history is preserved
		4. Non-volatile
			- Data isn't updated in real time, but refreshed on schedule (ex. nightly)
- **Lake**
	- Raw data in its native format at scale
	- Structure is only applied when data is queried
	- Risk of becoming a data swamp, without quality control or metadata
- **Lakehouse**
	- Combines low cost storage of a lake with ACID of a warehouse
	- Open table formats
	- Supports SQL analytics and ML on the same data
# Cloud computing
- Model for enabling ubiquitous and convenient on-demand access to a shared pool of computing resources
- 5 Key Characteristics
	1. On-demand self service
	2. Broad network access
	3. Resource pooling
	4. Rapid elasticity (of resources based on demand)
	5. Measured service (pay as you go)
# Cloud-based database solutions (diagrams)
- DBaaS
	- A fully managed DB by the provider
- DaaS
	- Provides the data itself as a service through APIs, but doesn't give an DBMS interface like SQL
- 5 DBaaS architectures
1. **Separate servers**
	- 1 server per tenant
	- Best for tenants with large DBs and many users
2. **Shared Server, Separate DB Processes**
	- Resources on one server machine are subdivided for each tenant
	- Each tenant still has their own DB server process
3. **Shared DBMS, separate DB**
	- One DB server shared by all tenants, each with their own DB
	- Single process can share resources like a DB cache, leading to fuller utilization of the machine
4. **Shared DB, Separate Schema**
	- One shared DB server, and each tenant's data is grouped into a schema created for that tenant
5. **Shared DB, shared schema**
	- Maximum sharing, lowest cost
	- A tenant ID column identifies whose row is whose
	- Best for a large number of tenants with a small number of servers
# Schema, system catalog, data directory, etc.
- **Schema**
	- A description of the DB structure
	- ANSI-SPARC has 3 schemas; external/conceptual/internal
- **System Catalogue**
	- Repository of metadata describing the data in the DB
# Degree and cardinality
- Degree is the number of attributes in a relation
	- Columns
- Cardinality
	- Number of tuples (rows) in a relation
# Relational model terminology (candidate key, primary key, foreign key, etc.)
- **Relation**
	- A table with columns and rows
	- Logical structure
- **Attribute**
	- A named column of a relation
- **Tuple**
	- A row of a relation
- **Domain**
	- The set of allowable rules for one or more attributes
- **Degree**
	- Number of attributes (columns)
- **Cardinality**
	- Number of tuples (rows)
- **Relational DB**
	- Collection of normalized relations with distinct names
- **Super Key**
	- An attribute or set of them that uniquely identifies a tuple
- **Candidate Key**
	- A super key with no proper subset
	- It is unique and irreducible
- **Composite Key**
	- A key made up of more than one attribute
- **Primary Key**
	- Candidate key selected to identify tuples uniquely within the relation, only one per table
	- Can't be NULL
- **Alternate Keys**
	- Candidate keys that weren't chosen as the primary key
- **Foreign Key**
	- An attribute or set of them within a relation that matches the candidate key of some relation
# NULL
- Null is a value for an attribute that is currently unknown or not applicable for a tuple
- Deals with incomplete or exceptional data
- Null is not:
	- Zero
	- An empty string
	- Spaces
- Null is the absence of a value
- Any comparison (>, <, =) with null returns null (unknown)
- Aggregate functions (SUM, AVG, etc.) eliminate nulls before operating
# Entity integrity and referential integrity
- **Entity Integrity**
	- In a base relation, no attribute of a primary key can be null
- **Referential Integrity**
	- If a foreign key exists in a relation, its value must either
		- Match a candidate key value of some tuple in its home
		- Be wholly null
- Referential integrity blocks inserting or updating a child row with a foreign key that has no matching parnet
	- Blocks deleting a