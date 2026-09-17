# Lecture
- Many applications for databases
	- Especially important in AI applications
		- RAG Pipelines, predictive analytics, ect.
- **Terms**
	- Database = DB
	- Knowledge Base = KB
	- Database Systems
	- Information Systems
	- Knowledge-Base Systems
	- Decision support systems
	- Metadata
	- Database management systems = DBMS
## Data
- Representation of observations suitable for processing and analysis
- Datum = given in the form of facts/text/symbols with meaning
## Information
- Data that has been processed, and can be used in decision making
- Information = processed data + purpose
			= data + meaning
- DIKW: Data --> Information --> Knowledge --> Wisdom
## Database
- A self-describing collection of integrated records
- Collection of related data
- DBMS: Database management system
	- Software enabling users to define, create, maintain, and control access to a DB
## Metadata
- Meta = About
- Metalanguage = language to describe other language
## File-Based Systems
- Collection of application programs that perform services for end user
	- a.k.a reports
- Computerizing the manual (physical) filing system
- Each program defines and manages its own data
## File-Based Processing
- There are many limitations to this method
	- Separates and isolates data
		- Each program maintains its own dataset
		- Each is unaware of useful data in other programs
	- Duplication of data
		- Same data held in multiple programs
	- Data dependence
		- File structure defined in program code
	- Incompatible file formats
	- Fixed queries/proliferation of application programs
		- Programs for specific functions
		- New requirement --> new program
	- Definition of data is embedded in application programs, rather than being stored independently
	- No control over access and manipulation beyond that imposed by the given application
## Database Approach
- Database Management System evolved to solve the file-based issues.
- **Database**: Shared collection of logically related data, designed to meet the needs of the organization
- **Metadata**: System catalogue, providing descriptions of data to enable program-data independence
- Logically related data comprises entities, attributes, and relationships of an organization's information
## Database Management Systems (DBMS)
- A software system enabling users to define, create, and maintain the DB
- Provides controlled access to a DB
- **Database Application Program**: A computer program which interacts with the DB by issuing requests to the DBMS
	- Requests are SQL statements
![](Pasted%20image%2020260917152503.png)
## Database Approach
- Data Definition Language (DDL)
	- Permits specification of data types, structures, and any data constraints
	- All specifications stored in DB
- Data Manipulation Language (DML)
	- Generic enquiry facility (query language) of the data
- Controlled access to the DB may include:
	1. Security systems
	2. Integrity systems
	3. Concurrency control
	4. Recovery control
	5. User-accessible catalog
	6. A view mechanism
		- Give users only the data they want/need
- **Views**
	- Allows each user to have their own view of the DB
	- A 'view' is essentially a subset of the DB
- Pros of views:
	- Reduced complexity
	- Security
	- Custom DB appearances
	- Consistent, unchanging experience of the database, even if the underlying structures change.
## Components of a DBMS Environment
- **Hardware**: Range from a PC to a network of computers
- **Software**: DBMS, OS, network software, and application programs
- **Data**: Used by the org and a description of this data (a schema)
- **Procedures**: Instructions and rules applied to the design and use of the DBMS
- **People**
## DBMS Roles
1. Data Administrator (DA)
	- Management of the data resources
2. Database Administrator (DBA)
	- Physical realization of the DB
	- Security/Integrity control, OS maintenance, performance
3. Database Designers (Logical/Physical)
	- Identifies data and the relationships between it
	- Chooses the constraints on the data that is to be stored
4. Application Developers
	- Implementing the application programs that provide usability
5. End Users (Naive vs. Sophisticated)
	- Clients of the DB, for whom it has been designed for
## History of DB Systems
1. 1950/60s
	- Hierarchical (IMS) and Network/CODASYL (IDS/IDMS) systems are developed
2. 1970s
	- Relational (RBDMS)
		- First commercial systems
3. 1980s
	- Object-relational (ORDBMS)
	- Object-oriented (OODBMS)
	- ISO SQL Standard
4. 1990s
	- Data warehousing systems appear
	- Web-DB integration
	- XML
## Advantages of DBMS
- Control of data redundancy & maintenance
- Data consistency, security, and integrity
- More information from the same amount of data
- Sharing data
- Enforceable standards
- Economies of scale
- Balanced conflicting requirments
- Improved data accessibility and responsiveness
- Increased productivity
## Disadvantages of DMBS
- Highly complex
- Large size
- Can be very expensive
- Hardware costs
- Cost to convert from paper
- High impact of system failures



# Textbook
