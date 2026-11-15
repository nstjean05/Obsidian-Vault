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
1. 



• DDL and DML
• Characteristics of views
• The components of DBMS environment
• Various roles (DA, DBA, Database Designer, Application Designer, End Users, etc.)
• Edgar F. Codd and Peter Chen
• ANSI-SPARC architecture (external level, conceptual, level, internal level, etc.)
• Three-tier client–server architecture (middle tier, middleware)
• Data independence (logical and physical)
• Different data models
• Identify what the diagram is about (Chapter 3
• File-server vs. client-server architectures
• Teleprocessing, web service, REST, SOA, microservices, NoSQL, NewSQL,
transaction processing monitor
• Distributed processing, distributed DBMS
• Data warehousing, data lake, and lakehouse
• Cloud computing
• Cloud-based database solutions (diagrams)CommentHighlight
• Schema, system catalog, data directory, etc.
• Degree and cardinality
• Relational model terminology (candidate key, primary key, foreign key, etc.)
• null
• Entity integrity and referential integrity
• Updates of a view
• Advantages and disadvantages of views
• PostgreSQL: basic and advanced (study both interactive and reference slides)
• PostgreSQL functions and triggers (PL/pgSQL)
• Relational algebra (operations, particularly join operations)
• Database system development lifecycle
• Users’ requirements specification and systems specification
• Fact-finding techniques
• ER diagrams (UML, Chen, and Crow’s feet notations) and multiplicities
• Two connection traps