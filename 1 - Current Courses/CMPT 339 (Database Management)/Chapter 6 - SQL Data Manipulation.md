# Purpose and Importance
- Retrieving data from DB using SELECT
- Use compound WHERE conditions
- Sort query results using ORDER BY
- Use aggregate functions
- Use subqueries
- Join tables
- Perform set operations (UNION, INTERSECT, EXCEPT)
- Update the DB using INSERT, UPDATE, and DELETE
# Objectives of SQL
- A DB language should allow users to create the DB and relation structures
- SQL is non-procedural
	- Specify what information you require, rather than how to get it
- SQL is free-format - parts of statements don't have to be typed in a specific location
- Consists of standard english words
```SQL
CREATE TABLE Staff(staffNo VARCHAR(5), IName VARCHAR (15), salary DECIMAL 7,2));

INSERT INTO Staff VALUES ('SG16', 'Brown', 8300);

SELECT staffNo, IName, salary
FROM Staff
WHERE salary > 10000;
```

# History of SQL
- E. F. Codd invented the relational model during his work at IBM's research lab in 1970
- 1974, D. Chamberlin defined SEQUEL
- 1976, revised version named SQL
- Oracle was the first commercial RDBMS based on SQL (1970s)
- SQL 2023 was the most recent update
- 