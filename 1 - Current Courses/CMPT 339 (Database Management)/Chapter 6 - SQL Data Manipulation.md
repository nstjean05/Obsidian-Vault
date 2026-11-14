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
# Writing SQL
- Reserved words - fixed part of SQL and must be spelt exactly as required for its function
- User-Defined words - Made up by user to represent names of various objects
	- Relations, columns, views
- Each clause should begin on a new line
- Parts of a clause are on new indented lines
	- None of this is necessary for function, but for readability
- Extended BNF notation
	- Upper case letters for reserved words
	- Lower case for user-defined words
	- | indicates a choice among alternatives
	- {} for a required element
	- [] for an optional element
	- ... for optional repetition (0 or more)
# Literals
- Literals are constants in SQL statements
	- Non-numerics are enclosed in single quotes
		- 'london'
	- Numerics aren't enclosed in quotes
		- 650.00
# SELECT
```sql
SELECT [DISTINCT | ALL]
FROM TableName[alias][,...]
WHERE condition
GROUP BY columnList HAVING condition
ORDER BY columnList
```
- **SELECT** specifies which columns are to appear in output
- **FROM** specifies table(s) to be used
- **WHERE** filters rows
- **GROUP BY** forms rows with same column value
- **HAVING** filters groups subject to some condition
- **ORDER BY** specifies the order of the output
- The order of the clauses cannot be changed
- Only SELECT and FROM are mandatory
- Example: List the full details of all staff
```sql
SELECT staffNo, fName, lName, position, sex, DOB, salary, branchNo
FROM Staff;

-- One may also use SELECT * to select all elements
```
![365](Pasted%20image%2020261114113625.png)
- Example: Produce a list of salaries for all staff, showing only staff number, first and last names, and salary
```sql
SELECT staffNo, fName, lName, salary
FROM Staff;
```
![293](Pasted%20image%2020261114113723.png)
- Example: List the property numbers of all properties that have been viewed
```sql
SELECT propertyNo
FROM Viewing;
```
![109](Pasted%20image%2020261114113936.png)
- Example: List distinct viewed property numbers
```sql
SELECT DISTINCT propertyNo
FROM Viewing;
```
![111](Pasted%20image%2020261114114024.png)
- Example: Produce list of monthly salaries for all staff, showing staff numbers, names, and salaries
```sql
SELECT staffNo, fName, lName, salary/12
FROM Staff
```
![285](Pasted%20image%2020261114114201.png)
- Example: Name a column using AS
	- AS creates an alias, a temp name for a column in the output
```sql
SELECT staffNo, fName, lName, salary/12 AS monthlySalary
FROM Staff
```
- Example: List all staff with a salary greater than 10,000
```sql
SELECT staffNo, fName, lName, salary
FROM Staff
WHERE salary > 10000;
```
- Example: List addresses of all branch offices in London or Glasgow
```sql
SELECT branchNo, street, city
FROM Branch
WHERE city = 'London' OR city = 'Glasgow'
```
- Example: List all staff with a salary between 20,000 and 30,000
```sql
SELECT staffNo, fName, lName, salary
FROM Staff
WHERE salary >= 20000 AND salary <= 30000;

-- Alternatively, use salary BETWEEN 20000 AND 30000;
```
![250](Pasted%20image%2020261114115346.png)
- Example: List all managers and supervisors
```sql
SELECT staffNo, fName, lName, position
FROM Staff
WHERE position = 'Manager' OR position = 'Supervisor';

-- Alternatively, use position IN('Manager', 'Supervisor')
```
- Example: List salaries for all staff, arranged in descending order of salary
```sql
SELECT staffNo, fName, lName, salary
FROM Staff
ORDER BY salary DESC;
```
- Example: Produce an abbreviated list of properties in order of property type
```sql
SELECT propertyNo, type_, rooms, rent
FROM PropertyForRent
ORDER BY type_;

--The _ after type occurs because type is a reserved word in SQL, and _ avoids it
```
![226](Pasted%20image%2020261114120205.png)
- Example: Further order the above by ordering the flats by rooms
```sql
SELECT propertyNo, type_, rooms, rent
FROM PropertyForRent
ORDER BY type_, rent DESC;
```
![228](Pasted%20image%2020261114120326.png)
# SELECT Aggregate statements
- 5 standard aggregate functions:
	- **COUNT** returns number of values in a column
	- **SUM** returns sum of values in a column
	- **AVG** returns the average of values in a column
	- **MIN** returns smallest val in a column
	- **MAX** returns largest value in a column
- Each operates on a single column of a table and returns a single value
- COUNT, MIN, and MAX apply to numeric and non-numeric, but SUM and AVG may only be used on numbers
- Apart from COUNT(`*`), each function eliminates NULLs first and operates on remaining values
- Example: How many properties cost more than 350/month to rent?
```SQL
SELECT COUNT(*) AS myCount
FROM PropertyForRent
WHERE rent > 350;
```
- Example: How many different properties were viewed in April 2025?
```SQL
SELECT COUNT(*) AS aprilViewing
FROM Viewing
WHERE viewDate BETWEEN '2015-04-01' AND '2015-04-28'

--Returns myCount 2
```
- Example: Find number of managers and the sum of their salaries
```SQL
SELECT COUNT(staffNo AS myCount),
	SUM(Salary) AS mySUM
FROM Staff
WHERE position = 'Manager'
```
![201](Pasted%20image%2020261114121910.png)
- Example: Find min, max, and avg staff salary
```sql
SELECT MIN(salary) AS minSalary,
	MAX(salary) AS minSalary,
	AVG(salary) AS avgSalary,
FROM Staff;
```
![248](Pasted%20image%2020261114141242.png)
# Select Statement for Grouping
- GROUP BY is used to get subtotals
- SELECT and GROUP BY are closely integrated
	- Each item in SELECT list must be single-valued per group, and select clause may only contain:
		- Col names
		- Aggregate functions
		- Constants
		- Expression involving combinations