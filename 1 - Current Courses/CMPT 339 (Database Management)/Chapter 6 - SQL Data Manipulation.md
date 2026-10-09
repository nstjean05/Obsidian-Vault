# SQL - Data Manipulation (PostgreSQL)
- All SQL here is written for PostgreSQL
- String literals use straight single quotes: `'London'`
- Use `COALESCE(expr, 0)` instead of `IFNULL()`
- Supports `FULL JOIN`, `INTERSECT`, and `EXCEPT` directly
- Does not implement `CORRESPONDING`
	- List columns explicitly in set operations
- Nested aggregates like `MAX(AVG(x))` are not allowed
	- Use a subquery instead
- Error messages shown are PostgreSQL messages
## Chapter Objectives
- Purpose and importance of SQL
- Retrieve data using `SELECT` with:
	- Compound `WHERE` conditions
	- `ORDER BY`
	- Aggregate functions
	- `GROUP BY` and `HAVING`
	- Subqueries
	- Joins
	- Set operations (`UNION`, `INTERSECT`, `EXCEPT`)
- Update the DB using `INSERT`, `UPDATE`, and `DELETE`
# Objectives of SQL
- Ideally, a database language should allow the user to:
	- Create the database and relation structures
	- Insert, modify, and delete data from relations
	- Perform simple and complex queries
- Must do these with minimal user effort
	- Command structure/syntax must be easy to learn
- Must be portable
- SQL is a **transform-oriented language** with 2 major components:
	- DDL for defining DB structure
	- DML for retrieving and updating data
- Until SQL:1999 (SQL3), no flow of control commands (IF...THEN...ELSE, GO TO, DO...WHILE)
	- Had to be done in a programming or job-control language, or interactively by the user
- Relatively easy to learn:
	- **Non-procedural** - specify *what* info you need, not *how* to get it
	- Essentially free-format - parts of statements don't have to be at particular screen locations
- Consists of standard English words:
	- `CREATE TABLE Staff(staffNo VARCHAR(5), lName VARCHAR(15), salary DECIMAL(7,2));`
	- `INSERT INTO Staff VALUES ('SG16', 'Brown', 8300);`
	- `SELECT staffNo, lName, salary FROM Staff WHERE salary > 10000;`
- Used by DBAs, management, app developers, and other end users
- ISO standard exists, making it the formal and de facto standard for relational DBs
# History of SQL
- Started with E. F. Codd's paper at IBM Research Laboratory in San José (Codd, 1970)
- 1974: D. Chamberlin (IBM San Jose) defined 'Structured English Query Language' (SEQUEL)
- 1976: SEQUEL/2 defined, name later changed to SQL for legal reasons
- IBM built a prototype DBMS called **System R**, based on SEQUEL/2
- Roots of SQL are in **SQUARE** (Specifying Queries as Relational Expressions), which predates System R
- Late 70s: ORACLE appeared, probably the first commercial SQL-based RDBMS
- Standards timeline:
	1. 1987 - ANSI and ISO publish initial standard
	2. 1989 - ISO addendum defining 'Integrity Enhancement Feature'
	3. 1992 - first major revision, SQL2 or SQL/92
	4. 1999 - SQL:1999, support for object-oriented data management
	5. 2003 - SQL:2003
	6. 2008 - SQL:2008
	7. 2011 - SQL:2011
	8. 2016 - SQL:2016
	9. June 2023 - SQL:2023
# Importance of SQL
- Part of application architectures like IBM's Systems Application Architecture
- Strategic choice of many large and influential orgs (ex. X/OPEN)
	- X/Open: Open Group for Unix Systems
- **Federal Information Processing Standard (FIPS)**
	- Conformance required for all sales of DBs to the American Government
- Used in other standards, and influences their development as a definitional tool
	- Ex. ISO's Information Resource Directory System (IRDS) Standard
	- Ex. Remote Data Access (RDA) Standard
# Writing SQL Commands
- A statement consists of reserved words and user-defined words
	- **Reserved words** are a fixed part of SQL
		- Must be spelt exactly as required
		- Cannot be split across lines
	- **User-defined words** are made up by the user
		- Represent names of DB objects like relations, columns, views
- Most components are case insensitive, except literal character data
- More readable with indentation and lineation:
	- Each clause begins on a new line
	- Start of a clause lines up with the start of other clauses
	- If a clause has several parts, each goes on a separate line, indented under the start of the clause
- Extended BNF (Backus-Naur form) notation:
	- Upper-case letters = reserved words
	- Lower-case letters = user-defined words
	- `|` = choice among alternatives
	- Curly braces `{}` = required element
	- Square brackets `[]` = optional element
	- `...` = optional repetition (0 or more)
## Literals
- Constants used in SQL statements
- All non-numeric literals must be in single quotes (ex. `'London'`)
- All numeric literals must not be in quotes (ex. `650.00`)
# SELECT Statement
- `SELECT [DISTINCT | ALL] {* | [columnExpression [AS newName]] [,...]} FROM TableName [alias] [,...] [WHERE condition] [GROUP BY columnList] [HAVING condition] [ORDER BY columnList]`
- **SELECT** - specifies which columns appear in output
- **FROM** - specifies table(s) to be used
- **WHERE** - filters rows
- **GROUP BY** - forms groups of rows with the same column value
- **HAVING** - filters groups subject to some condition
- **ORDER BY** - specifies the order of the output
- Order of the clauses cannot be changed
- Only `SELECT` and `FROM` are mandatory
## Example 6.1 All Columns, All Rows
- List full details of all staff
- `SELECT staffNo, fName, lName, position, sex, DOB, salary, branchNo FROM Staff;`
- Can use `*` as shorthand for 'all columns'
	- `SELECT * FROM Staff;`
## Example 6.2 Specific Columns, All Rows
- List staff number, first and last names, and salary for all staff
- `SELECT staffNo, fName, lName, salary FROM Staff;`
## Example 6.3 Use of DISTINCT
- List property numbers of all properties that have been viewed
- `SELECT propertyNo FROM Viewing;`
- Use `DISTINCT` to eliminate duplicates
	- `SELECT DISTINCT propertyNo FROM Viewing;`
## Example 6.4 Calculated Fields
- List monthly salaries for all staff
- `SELECT staffNo, fName, lName, salary/12 FROM Staff;`
- To name the column, use `AS`
	- `SELECT staffNo, fName, lName, salary/12 AS monthlySalary FROM Staff;`
## Example 6.5 Comparison Search Condition
- List all staff with a salary greater than 10,000
- `SELECT staffNo, fName, lName, position, salary FROM Staff WHERE salary > 10000;`
## Example 6.6 Compound Comparison Search Condition
- List addresses of all branch offices in London or Glasgow
- `SELECT * FROM Branch WHERE city = 'London' OR city = 'Glasgow';`
## Example 6.7 Range Search Condition
- List all staff with a salary between 20,000 and 30,000
- `SELECT staffNo, fName, lName, position, salary FROM Staff WHERE salary BETWEEN 20000 AND 30000;`
- `BETWEEN` includes the endpoints of the range
- Negated version: `NOT BETWEEN`
- Doesn't add much to SQL's expressive power
	- Could write `WHERE salary >= 20000 AND salary <= 30000`
	- Useful for a range of values
## Example 6.8 Set Membership
- List all managers and supervisors
- `SELECT staffNo, fName, lName, position FROM Staff WHERE position IN ('Manager', 'Supervisor');`
- Negated version: `NOT IN`
- Doesn't add much to SQL's expressive power
	- Could write `WHERE position = 'Manager' OR position = 'Supervisor'`
	- `IN` is more efficient when the set contains many values
## Example 6.9 Pattern Matching
- Find all owners with the string 'Glasgow' in their address
- `SELECT ownerNo, fName, lName, address, telNo FROM PrivateOwner WHERE address LIKE '%Glasgow%';`
- 2 special pattern matching symbols:
	- `%` - sequence of zero or more characters
	- `_` (underscore) - any single character
- `LIKE '%Glasgow%'` means a sequence of characters of any length containing 'Glasgow'
## Example 6.10 NULL Search Condition
- List details of all viewings on property PG4 where a comment has not been supplied
- 2 viewings for PG4, one with and one without a comment
- Must test for null explicitly with `IS NULL`
	- `SELECT clientNo, viewDate FROM Viewing WHERE propertyNo = 'PG4' AND comment_ IS NULL;`
- Negated version (`IS NOT NULL`) tests for non-null values
## Example 6.11 Single Column Ordering
- List salaries for all staff in descending order of salary
- `SELECT staffNo, fName, lName, salary FROM Staff ORDER BY salary DESC;`
- For ascending order, use `ASC`
## Example 6.12 Multiple Column Ordering
- List properties in order of property type
- `SELECT propertyNo, type_, rooms, rent FROM PropertyForRent ORDER BY type_;`
- Four flats in the list
	- No minor sort key specified, so the system arranges these rows in any order it chooses
- To order by rent, specify a minor order
	- `SELECT propertyNo, type_, rooms, rent FROM PropertyForRent ORDER BY type_, rent DESC;`
# SELECT Statement - Aggregates
- ISO defines 5 aggregate functions:
	- **COUNT** - number of values in the specified column
	- **SUM** - sum of values in the specified column
	- **AVG** - average of values in the specified column
	- **MIN** - smallest value in the specified column
	- **MAX** - largest value in the specified column
- Each operates on a single column and returns a single value
- `COUNT`, `MIN`, `MAX` apply to numeric and non-numeric fields
	- `SUM` and `AVG` are numeric only
- Apart from `COUNT(*)`, each function eliminates nulls first and operates only on the remaining non-null values
- `COUNT(*)` counts all rows, regardless of nulls or duplicates
- Can use `DISTINCT` before the column name to eliminate duplicates
	- No effect with `MIN`/`MAX`, but may have one with `SUM`/`AVG`
- Commonly used in the `SELECT` list and `HAVING` clause
	- PostgreSQL also permits them in contexts like `ORDER BY`
- What is the difference between these two?
	- `SELECT staffNo, COUNT(salary) FROM Staff;`
	- `SELECT staffNo, COUNT(salary) FROM Staff GROUP BY salary;`
## Example 6.13 Use of COUNT(*)
- How many properties cost more than £350 per month to rent?
- `SELECT COUNT(*) AS myCount FROM PropertyForRent WHERE rent > 350;`
## Example 6.14 Use of COUNT(DISTINCT)
- How many different properties were



1. Suppose that a packet-switched network is used and the only traffic in this network comes from such applications as described above. Furthermore, assume that the sum of the application data rates is less than the capacities of each and every link. Is some form of congestion control needed? Why?
Congestion control wouldn't be needed in this scenario, since each of the links has excess capacity. This means that there won't be any congestion to worry about.    

  
  

P7. In this problem, we consider sending real-time voice from Host A to Host B over a packet-switched network (VoIP). Host A converts analog voice to a digital 64 kbps bit stream on the fly. Host A then groups the bits into 56-byte packets. There is one link between Hosts A and B; its transmission rate is 10 Mbps and its propagation delay is 10 msec. As soon as Host A gathers a packet, it sends it to Host B. As soon as Host B receives an entire packet, it converts the packet’s bits to an analog signal. How much time elapses from the time a bit is created (from the original analog signal at Host A) until the bit is decoded (as part of the analog signal at Host B)?



  

P11. In the above problem, suppose R_1 = R_2 = R_3 = R and d_proc = 0. Further suppose that the packet switch does not store-and-forward packets but instead immediately transmits each bit it receives before waiting for the entire packet to arrive. What is the end-to-end delay?