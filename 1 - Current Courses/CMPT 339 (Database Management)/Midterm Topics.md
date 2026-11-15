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