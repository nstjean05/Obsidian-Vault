# Lecture
### Overview
- DB systems are intended to provide users with an abstracted view of the data
- The DB's design must start with an abstract and general description of the information requirements of the organization
- Each user may need to have a different view of the data
- To satisfy this, most modern DBMS are built on the **ANSI-SPARC** architecture
- **Schema**: Structural framework or blueprint that defines how data is organized, stored, and accessed within a DB
## Objectives of 3-Level Architectures
- All users should be able to access the same data
- A user's view is immune to changes made in other views
- Users don't need to know physical DB storage info
- DBA should be able to change the underlying structure without affecting user views
- DB structure should be unaffected by physical storage changes
- DBA should be able to change conceptual structure of the DB without affecting all users
## ANSI-SPARC 3-Level Architecture
![](Pasted%20image%2020260917155136.png)
![](Pasted%20image%2020260917155731.png)
### External
- Users' DB view
- Describes the part of the DB relevant to a particular user
- Different views have different representations of the same data
	- Ex. Regional display of day/month/year vs. year/month day
- Some views may have derived/calculated data
	- Ex. displaying age from date of birth data
### Conceptual
- Community/Logical view of the DB
- Describes *what* data is stored in the DB and their relationships
- Provides mapping and independence between external/internal
- Represents:
	- All entities, their attributes, and relationships
	- Constraints on data
	- Semantic info on data
	- Security/integrity info
### Internal
- Physical representation/implementation of the DB on the computer
- Describes *how* the data is stored
- Covers the data structures and file orgs
- Concerned with:
	- Storage space allocation
	- Record descriptions of data for storage
	- Data placement
	- Data compression and encryption
## Data Independence
- **Logical Independence**
	- Immunity of external schemas to changes in the conceptual schema
	- Conceptual schema changes should not require changes to external schema
- **Physical Independence**
	- Refers to the immunity of conceptual schema to changes in the internal schema
	- Internal schema changes shouldn't necessitate changes to conceptual or external schemas
## Database Languages
### Data Definition Language (DDL)
- Allows the database admin (DBA) or user to describe and name entities/attributes/relationships
- Specifies/defines the database schema
- Doesn't manipulate data
- Result of compiling DDL statements is a set of *tables* stored in special files collectively called the system catalog or data dictionary
	- This catalog integrates the metadata that describes the objects in the DB
### Data Manipulation Language (DML)
- Provides basic data manipulation operations on data held in the DB
- Data manipulation operations include the following:
	- Insertion/Modification/Retrieval/Deletion of data stored in the DB
- Query Language: part of a DML that involves data retrieval
- Procedural DML
	- Allows user to tell system *how* to manipulate data
- Non-Procedural DML
	- Declarative
	- Allows user to state *what* data is needed rather than how it is retrieved
	- e.g. SQL or QBE (query-by-example)
## Data Models
- DDL is used to write a schema, but is too low level
- Data model:
	- A higher-level description of the schema
	- Integrated collection of concepts for describing data/relationships/constraints
- Data model comprises:
	- Structural part --> A set of rules
	- Manipulative part --> Types of operation (update/receive data)
	- An optional set of integrity rules to ensure the accuracy of the data
- Modelling answers "What should the DB represent?"
- DDL answers "How do I create that representation in the DBMS"
- Purpose: Represent data in an understandable way
- Categories include:
	- Object-based (conceptual & internal levels)
	- Record-based (conceptual & internal levels)
	- Physical (internal level)
### Object-Based Data Models
- Concepts like entities, attributes, and relationships
	- **Entity**: A distinct object in the organization that is to be represented in the DB
	- **Attribute**: A property that describes some aspect of the object we wish to record
	- **Relationship**: An association between entities
- Common types:
	- Entity-relationship (ER)
	- Semantic
	- Functional
	- Object-oriented
### Record-Based Data Models
- Fixed-format records
- **Relational Data Model** (declarative)
	- Based on mathematical relations
	- Data and relationships are represented as tables
- **Network Data Model** (navigational approach)
	- Data is represented as collections of records
	- Relationships are represented as sets
- **Hierarchical Model** (navigational approach)
	- A restricted type of network model
	- Allows a node to have only one parent (tree graph)
### Physical Data Models
- Describe how data is stored in the computer, representing information such as record structures, record orderings, and access paths
## Conceptual Modelling
- Conceptual Schema:
	- Heart of the DB (core system)
	- Supports all the external views and is supported by the internal schema
	- Should be complete and accurate representation of an organization's data requirements
- Conceptual modelling is the process of developing a model of information use that is independent of implementation details
- Resulting in a conceptual data model
## 10 Functions of a DBMS
1. Data storage, retrieval, and updates
2. A user-accessible catalog
3. Transaction support
4. Concurrency control
5. Recovery services
6. Auth services
7. Support for data communication software
8. Integrity services
9. Services to p