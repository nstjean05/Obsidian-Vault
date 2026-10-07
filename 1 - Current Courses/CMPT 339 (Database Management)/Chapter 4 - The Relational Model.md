## RDBMS
- Relational Database Management Systems
- They remain the dominant and most widely used DB technology
## Relational Model Terminology
- A **relation** is a table with columns and rows
	- Only applies to the logical structure of the DB
- An **attribute** is a named column of a relation
- A **domain** is the set of allowable values for one or more attributes
- **Tuple** is a row of a relation
- **Degree** is the number of attributes in a relation
- **Cardinality** is the number of tuples in a relation
- **Relational DB** is a collection of normalized relations, with distinct relation names
- **Normalization** indicates no repeated groups (redundancy)
![](z.%20Images/Pasted%20image%2020260930211037.png)
![](z.%20Images/Pasted%20image%2020260930211051.png)
## Mathematical Definition of a Relation
- Example: D = {2,4} and E = {1,3,5}
	- D * E = {(2,1), (2,3), (2,5), (4,1), (4,3), (4,5)}
- Any subset of a cartesian product is a relation
	- R = {(2,1), (2,3)} is a subset of D * E
# Database Relations
- **Relational Database Schema**
	- Set of relation schemas, each with a distinct name
	- If R1, R2, ..., Rn are relation schemas, the relational schema R is written as:
		- R = (R1, R2, ..., Rn)
## Properties of Relations
- Relation name is distinct from all other relation names in the schema
- Each cell contains exactly one atomic (single) value
- Each attribute has a distinct name
- Values of an attribute all come from the same domain
- Each tuple is distinct, so there are no duplicate tuples
- Order of attributes has no significance
- Order of tuples has no significance in theory
	- In practice, physical ordering and indexing matter for performance
# Relational Keys
- **Superkey**
	- An attribute, or set of attributes, that uniquely identifies a tuple within a relation
- **Candidate Key**
	- A superkey (K) where no proper subset is a superkey (a minimal superkey)
	- Uniqueness - values of K uniquely identify each tuple of R
	- Irreducibility - no proper subset of K has the uniqueness property
- **Composite Key**
	- A key made up of more than one attribute
- **Primary Key**
	- The candidate key selected to uniquely identify tuples within the relation
- **Alternate Keys**
	- Candidate keys that were not selected as the primary key
- **Foreign Key**
	- An attribute, or set of attributes, in one relation that matches the candidate key of some (possibly the same) relation
## Proper Subset
- Set A is a proper subset of set B (A ⊂ B) if and only if:
	1. A is a set
	2. Every element of A is also an element of B
	3. A ≠ B
# Integrity Constraints
- **Null**
	- Represents a value for an attribute that is currently unknown or not applicable for the tuple
	- Deals with incomplete or exceptional data
	- Represents the absence of a value
		- Not the same as zero or spaces, which are values
	- SQL implements ternary logic to handle NULL
		- Three-valued logic (true, false, NULL)
- **General Constraints**
	- Additional rules specified by users or DB admins that define or constrain some aspect of the enterprise
	- Ex. an upper limit of 20 on the number of staff at a branch office
# Views
- **Base Relation**
	- Named relation corresponding to an entity in the conceptual schema
	- Its tuples are physically stored in the database
- **View**
	- The dynamic result of one or more relational operations on base relations, producing another relation
	- A virtual or derived relation that doesn't necessarily exist in the DB
		- Produced upon request, at the time of request
	- Contents are defined as a query on one or more base relations
	- Dynamic, so changes to base relations that affect view attributes are immediately reflected in the view
## Purpose of Views
- Powerful and flexible security mechanism by hiding parts of the DB from certain users
- Lets users access data in a customized way
	- The same data can be seen by different users in different ways, at the same time
- Can simplify complex operations on base relations
## Updating Views
- Updates to a base relation should be immediately reflected in all views that reference it
- If a view is updated, the underlying base relation should reflect the change
- Restrictions on modifications made through views:
	- Allowed if the query involves a single base relation and contains a primary key or candidate key of that base relation
	- Not allowed if it involves multiple base relations
	- Not allowed if it involves aggregation or grouping operations
![](z.%20Images/Pasted%20image%2020260929181339.png)




**Client**

|clientNo|fName|
|---|---|
|CR56|Aline|
|CR74|Mike|
|CR76|John|

**Viewing**

| clientNo | propertyNo |
| -------- | ---------- |
| CR56     | PA14       |
| CR56     | PG4        |
| CR76     | PG4        |
| CR62     | PA14       |