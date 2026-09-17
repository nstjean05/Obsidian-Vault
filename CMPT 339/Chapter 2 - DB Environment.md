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
- Allows