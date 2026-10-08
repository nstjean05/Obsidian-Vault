# Relational Algebra and Relational Calculus
## Chapter Objectives
- Meaning of the term **relational completeness**
- How to form queries in relational algebra
- Basic concepts of tuple and domain relational calculus (intro only)
- Categories of relational DML
# Introduction
- Relational algebra and relational calculus are formal languages associated with the relational model
- Informally:
	- Relational algebra is a (high-level) **procedural** language
	- Relational calculus is a **non-procedural** language
- Formally, both are equivalent to one another
- A language that produces a relation that can be derived using relational calculus is **relationally complete**
## "Relationally Complete"
- A query language is relationally complete if it can express every query that relational algebra can
	- Codd's benchmark for "as powerful as the relational model itself"
- When a language (like SQL, or safe relational calculus) is called relationally complete:
	- Anything you can compute with σ, Π, ∪, −, ×, joins, etc. can also be written in that language
- Nothing more, nothing less
	- About expressive power, not performance or usability
# Relational Algebra
- Operations work on one or more relations to define another relation without changing the originals
- Both operands and results are relations, so the output of one operation can be the input to another
- Allows expressions to be nested, just like arithmetic
	- This property is called **closure**
- 5 basic operations:
	1. Selection
	2. Projection
	3. Cartesian product
	4. Union
	5. Set Difference
- These perform most of the data retrieval operations needed
- Also have Join, Intersection, and Division
	- Can be expressed in terms of the 5 basic operations
## Selection (or Restriction)
- `σpredicate(R)`
- Works on a single relation R
- Defines a relation containing only the tuples (rows) of R that satisfy the specified condition (predicate)
- Ex. List all staff with a salary greater than £10,000
	- `σsalary > 10000(Staff)`
## Projection
- `Πcol1, ..., coln(R)`
- Works on a single relation R
- Defines a relation containing a vertical subset of R
	- Extracts the values of the specified attributes
	- Eliminates duplicates
- Ex. List staffNo, fName, lName, and salary for all staff
	- `ΠstaffNo, fName, lName, salary(Staff)`
## Union
- `R ∪ S`
- Defines a relation containing all tuples of R, or S, or both, with duplicates eliminated
- R and S must be **union-compatible**
	- Same attributes and essentially the same types, but can have different names and values
- If R and S have I and J tuples, union is obtained by concatenating them into one relation
	- Maximum of (I + J) tuples
- Ex. List all cities where there is either a branch office or a property for rent
	- `Πcity(Branch) ∪ Πcity(PropertyForRent)`
## Set Difference
- `R - S`
- Defines a relation of the tuples that are in R but not in S
- R and S must be union-compatible
- Ex. List all cities where there is a branch office but no properties for rent
	- `Πcity(Branch) - Πcity(PropertyForRent)`
## Intersection
- `R ∩ S`
- Defines a relation of all tuples that are in both R and S
- R and S must be union-compatible
- Expressed using basic operations:
	- `R ∩ S = R - (R - S)`
- Ex. List all cities where there is both a branch office and at least one property for rent
	- `Πcity(Branch) ∩ Πcity(PropertyForRent)`
## Cartesian Product
- `R × S`
- Defines a relation that is the concatenation of every tuple of R with every tuple of S
- Ex. List the names and comments of all clients who have viewed a property for rent
	- `(ΠclientNo, fName, lName(Client)) × (ΠclientNo, propertyNo, comment(Viewing))`
- Use Selection to extract the tuples where `Client.clientNo = Viewing.clientNo`
	- `σClient.clientNo = Viewing.clientNo((ΠclientNo, fName, lName(Client)) × (ΠclientNo, propertyNo, comment(Viewing)))`
- Cartesian product and Selection can be reduced to a single operation called a **Join**
# Join Operations
- Join is a derivative of Cartesian product
- Equivalent to a Selection, using the join predicate as the selection formula, over the Cartesian product of the two operand relations
- One of the most difficult operations to implement efficiently in an RDBMS
	- One reason RDBMSs have intrinsic performance problems
- Various forms:
	- Theta join
	- Equijoin (a particular type of Theta join)
	- Natural join
	- Outer join
	- Semijoin
## Theta Join (θ-join)
- `R ⋈F S`
- Defines a relation containing tuples satisfying the predicate F from the Cartesian product of R and S
- F is of the form `R.ai θ S.bi`
	- θ may be one of the comparison operators (<, ≤, >, ≥, =, ≠)
- Can be rewritten using basic Selection and Cartesian product:
	- `R ⋈F S = σF(R × S)`
- **Degree** of a Theta join is the sum of the degrees of the operand relations R and S
	- `degree(R ⋈ S) = degree(R) + degree(S)`
	- Ex. R(a, b) has degree 2 and S(c, d, e) has degree 3
		- `R ⋈R.a = S.c S` has degree 5, with attributes (a, b, c, d, e)
- If F contains only equality (=), the term **Equijoin** is used
## Equijoin
- Ex. List the names and comments of all clients who have viewed a property for rent
	- `(ΠclientNo, fName, lName(Client)) ⋈Client.clientNo = Viewing.clientNo (ΠclientNo, propertyNo, comment(Viewing))`
## Natural Join
- `R ⋈ S`
- An Equijoin of R and S over all common attributes x
	- One occurrence of each common attribute is eliminated from the result
- `R ⋈ S = Πwithout duplicate x's(R ⋈R.x = S.x S)`
- Ex. List the names and comments of all clients who have viewed a property for rent
	- `(ΠclientNo, fName, lName(Client)) ⋈ (ΠclientNo, propertyNo, comment(Viewing))`
## Outer Join
- Used to display rows in the result that do not have matching values in the join column
- `R ⟕ S`
- **Left (natural) Outer join** - keeps every tuple in the left-hand relation
	- Tuples from R without matching values in the common columns of S are also included
- **Right Outer join** - keeps every tuple in the right-hand relation
- **Full Outer join** - keeps all tuples in both relations
	- Pads tuples with nulls when no matching tuples are found
- Ex. Produce a status report on property viewings
	- `ΠpropertyNo, street, city(PropertyForRent) ⟕ Viewing`
## Semijoin (Semi-Theta Join)
- `R ⋉F S`
- Defines a relation containing the tuples of R that participate in the join of R with S
- Can be rewritten using Projection and Join:
	- `R ⋉F S = ΠA(R ⋈F S)`
	- A is the set of all attributes of R
- Ex. List complete details of all staff who work at the branch in Glasgow
	- `Staff ⋉Staff.branchNo = Branch.branchNo(σcity = 'Glasgow'(Branch))`
## Rename
- `ρS(E)` or `ρS(a1, a2, ..., an)(E)`
- Gives a new name S to the expression E
	- Optionally names the attributes as a1, a2, ..., an
- Ex. Rename the attributes Name, Age of table Department to A, B
- Ex. Rename the table Project to Pro and its attributes to P, Q, R
- Ex. Rename the first attribute of table Student (A, B, C) to P
- Ex. Rename the relation Student as Male Student, and its attributes RollNo, SName as (Sno, Name)
## Division
- `R ÷ S`
- Defines a relation over the attributes C consisting of the set of tuples from R that match the combination of every tuple in S
- Expressed using basic operations:
	- `T1 ← ΠC(R)`
	- `T2 ← ΠC((S × T1) - R)`
	- `T ← T1 - T2`
- Ex. Identify all clients who have viewed all properties with three rooms
	- `(ΠclientNo, propertyNo(Viewing)) ÷ (ΠpropertyNo(σrooms = 3(PropertyForRent)))`
## Aggregate Operations
- `ℑAL(R)`
- Applies the aggregate function list, AL, to R to define a relation over the aggregate list
- AL contains one or more (`<aggregate_function>`, `<attribute>`) pairs
- Main aggregate functions: COUNT, SUM, AVG, MIN, MAX
- Ex. How many properties cost more than £350 per month to rent?
	- `ρR(myCount) ℑCOUNT propertyNo(σrent > 350(PropertyForRent))`
## Grouping Operation
- `GAℑAL(R)`
- Groups tuples of R by the grouping attributes, GA, then applies the aggregate function list, AL, to define a new relation
- Resulting relation contains the grouping attributes, GA, along with the results of each aggregate function
- Ex. Find the number of staff working in each branch and the sum of their salaries
	- `ρR(branchNo, myCount, mySum) branchNo ℑCOUNT staffNo, SUM salary(Staff)`
	- ρR is renaming
# Relational Calculus
- A query specifies *what* is to be retrieved rather than *how*
	- No description of how to evaluate a query
- In first-order logic (predicate calculus), a **predicate** is a truth-valued function with arguments
- When values are substituted for the arguments, the function yields a **proposition**
	- Can be either true or false
- If a predicate contains a variable (ex. 'x is a member of staff'), there must be a range for x
	- Some values of the range may make the proposition true, others false
- Two forms when applied to databases: tuple and domain
- Logical connectives:
	- `∧` (AND)
	- `∨` (OR)
	- `~` (NOT)
## Tuple Relational Calculus
- Interested in finding tuples for which a predicate is true
- Based on **tuple variables**
	- A variable that 'ranges over' a named relation
	- Only permitted values are tuples of the relation
- To specify the range of a tuple variable S as the Staff relation:
	- `Staff(S)`
- To find the set of all tuples S such that F(S) is true:
	- `{S | F(S)}`
	- F is a formula (well-formed formula or wff)
- Ex. Find details of all staff earning more than £10,000
	- `{S | Staff(S) ∧ S.salary > 10000}`
- Ex. Find a particular attribute, such as salary
	- `{S.salary | Staff(S) ∧ S.salary > 10000}`
## Domain Relational Calculus
- Uses variables that take values from domains instead of tuples of relations
- If F(d1, d2, ..., dn) is a formula composed of atoms, and d1, d2, ..., dn are domain variables:
	- `{d1, d2, ..., dn | F(d1, d2, ..., dm)}` is a general domain relational calculus expression
- Ex. Find the names of all managers who earn more than £25,000
	- `{fN, lN | (∃sN, posn, sex, DOB, sal, bN)(Staff(sN, fN, lN, posn, sex, DOB, sal, bN) ∧ posn = 'Manager' ∧ sal > 25000)}`
	- Shorthand: `(∃d1, d2, ..., dn)` in place of `(∃d1, ∃d2, ..., ∃dn)`
- When restricted to **safe expressions**, domain relational calculus is equivalent to tuple relational calculus restricted to safe expressions, which is equivalent to relational algebra
	- Every relational algebra expression has an equivalent relational calculus expression, and vice versa
	- An expression is safe if all values that appear in the result are values from the domain of the expression
# Other Languages
- **Transform-oriented languages**
	- Non-procedural languages that use relations to transform input data into required outputs
	- Ex. SQL
- **Graphical languages**
	- Give the user a picture of the structure of the relation
	- User fills in an example of what is wanted and the system returns the required data in that format
	- Ex. QBE
- **4GLs**
	- Can create a complete customized application using a limited set of commands in a user-friendly, often menu-driven environment
- **5GLs**
	- Some systems accept a form of natural language
	- Still at an early stage
## Homework 2
**Part 1**
a. $\Pi_{\text{equipNo, description, dailyRate}}(\sigma_{\text{category} = vision}(\text{Equipment}))$
b. $\Pi_{\text{firstName, lastName}}(\sigma_{(\text{year} \geq 3) \,\land\, (\text{program = Computing Science})}(\text{Student}))$
c. $\Pi_{\text{equipNo, description}}(\sigma_{\text{dailyRate} ≤ 18}(\text{Equipment}))$
d. $\Pi_{\text{studentNo, firstName, lastName, description}}\big((\text{Student} \bowtie \text{Loan}) \bowtie \text{Equipment}\big)$
e. $\Pi_{\text{equipNo, description, firstName, lastName}}\big(\text{Equipment} ⟕ ((\text{Loan} - \sigma_{\text{dateReturned} \geq \text{dateOut}}(\text{Loan})) \bowtie \text{Student})\big)$
f. $\Pi_{\text{studentNo}}\big(\text{Loan})$
g. $\Pi_{\text{studentNo, equipNo}}(\text{Loan}) \div \Pi_{\text{equipNo}}(\sigma_{\text{category = VR}}(\text{Equipment}))$

**Part 2**
Relational algebra evaluation and reasoning. Using the database instance above, show the resulting relation for each expression. For each answer, show the intermediate relation produced after each major operator and write one short sentence explaining why that operator is used.

a. $\sigma_{\text{category = Vision} \,\land\, \text{dailyRate} \leq 20}(\text{Equipment})$
	The only column of the $\land$ that resulted with a true match value in both vision and dailyRate was E201.

| equipNo | description  | category | dailyRate | labNo |
| ------- | ------------ | -------- | --------- | ----- |
| E201    | Depth Camera | Vision   | 18        | L02   |

b. $\Pi_{\text{studentNo, description}}(\text{Loan} \bowtie \text{Equipment})$
	First, we take the natural join of *Loan* and *Equipment*, matching based on *equipNo*. Then $\Pi$ filters to display the two relevant columns, *studentNo* and *description*.

| loanNo | equipNo | studentNo | dateOut   | dateDue   | dateReturned | description       | category      | dailyRate | labNo |
| ------ | ------- | --------- | --------- | --------- | ------------ | ----------------- | ------------- | --------- | ----- |
| LN01   | E101    | S101      | 10-Sep-26 | 12-Sep-26 | 12-Sep-26    | VR Headset 01     | VR            | 25        | L01   |
| LN02   | E201    | S102      | 11-Sep-26 | 14-Sep-26 | NULL         | Depth Camera      | Vision        | 18        | L02   |
| LN03   | E301    | S103      | 09-Sep-26 | 13-Sep-26 | 13-Sep-26    | Braille Display   | Accessibility | 12        | L03   |
| LN04   | E102    | S101      | 15-Sep-26 | 18-Sep-26 | NULL         | VR Headset 02     | VR            | 25        | L01   |
| LN05   | E302    | S104      | 12-Sep-26 | 15-Sep-26 | 15-Sep-26    | Haptic Controller | Haptics       | 15        | L04   |
| LN06   | E303    | S103      | 14-Sep-26 | 16-Sep-26 | NULL         | 3D Scanner        | Fabrication   | 20        | L04   |

c. $\Pi_{\text{studentNo, firstName, lastName}}\big(\sigma_{\text{dateReturned = NULL}}(\text{Loan}) \bowtie \text{Student}\big)$
	First, we filter down to the loans that specifically have no return date. Then, we use the natural join to connect *studentNo* to the loans, keeping *firstName*, *lastName*, *program*, and *year*. Finally, we use $\Pi$ to keep just the three relevant terms.

| loanNo | equipNo | studentNo | dateOut   | dateDue   | dateReturned |     |
| ------ | ------- | --------- | --------- | --------- | ------------ | --- |
| LN02   | E201    | S102      | 11-Sep-26 | 14-Sep-26 | NULL         |     |
| LN04   | E102    | S101      | 15-Sep-26 | 18-Sep-26 | NULL         |     |
| LN06   | E303    | S103      | 14-Sep-26 | 16-Sep-26 | NULL         |     |

| loanNo | equipNo | studentNo | dateOut   | dateDue   | dateReturned | firstName | lastName | program           | year |
| ------ | ------- | --------- | --------- | --------- | ------------ | --------- | -------- | ----------------- | ---- |
| LN02   | E201    | S102      | 11-Sep-26 | 14-Sep-26 | NULL         | Ethan     | Wong     | Computing Science | 2    |
| LN04   | E102    | S101      | 15-Sep-26 | 18-Sep-26 | NULL         | Mina      | Choi     | Computing Science | 3    |
| LN06   | E303    | S103      | 14-Sep-26 | 16-Sep-26 | NULL         | Sara      | Patel    | Mathematics       | 3    |
