#AISummary 
## 5.1 Introduction
- **Relational algebra** and **relational calculus** are formal languages tied to the relational model
    - Algebra: (high-level) _procedural_, how to get the result
    - Calculus: _non-procedural_, what to get
    - Formally, both are equivalent
- **Relationally complete**: a language that can produce any relation derivable using relational calculus
    - Codd's benchmark for "as powerful as the relational model itself"
    - Can express anything algebra can (σ, Π, ∪, −, ×, joins, etc.)
    - Ex. SQL, safe relational calculus
    - About _expressive power_, not performance or usability
    - Nothing more, nothing less
### 5.1.1 Objectives
- Meaning of relational completeness
- How to form queries in relational algebra
- Basic concepts of tuple and domain relational calculus (intro only)
- Categories of relational DML
## 5.2 Relational Algebra
- Ops work on one or more relations to define another relation **without changing the originals**
- Operands and results are both relations, so output of one op can be input to another
- Lets expressions nest, like arithmetic. This property is called **closure**
- Five basic operations:
    1. Selection
    2. Projection
    3. Cartesian product
    4. Union
    5. Set difference
- Cover most data retrieval needs
- Join, Intersection, and Division are derived, can be expressed w/ the 5 basics
- Aside: slide examples all use the DreamHome schema (Staff, Branch, Client, Viewing, PropertyForRent)
### 5.2.1 Selection (or Restriction)
- **$\sigma_{\text{predicate}}(R)$**
- Works on a single relation R
- Returns only the tuples (rows) of R that satisfy the predicate
- Horizontal subset
- Ex. list all staff with salary > £10,000
    - $\sigma_{\text{salary} > 10000}(\text{Staff})$
### 5.2.2 Projection
- **$\Pi_{col_1, \ldots, col_n}(R)$**
- Works on a single relation R
- Returns a vertical subset of R, extracting values of the specified attributes
- _Eliminates duplicates_
- Ex. list staffNo, fName, lName, salary for all staff
    - $\Pi_{\text{staffNo, fName, lName, salary}}(\text{Staff})$
### 5.2.3 Union
- **$R \cup S$**
- All tuples in R, or S, or both, duplicates eliminated
- R and S must be **union-compatible**
    - Same attributes and essentially same types
    - Names and values can differ
- If R has I tuples and S has J tuples, result has at most (I + J) tuples
- Ex. all cities with either a branch office or a property for rent
    - $\Pi_{\text{city}}(\text{Branch}) \cup \Pi_{\text{city}}(\text{PropertyForRent})$
### 5.2.4 Set Difference
- **$R - S$**
- Tuples in R but not in S
- R and S must be union-compatible
- Ex. cities with a branch office but no properties for rent
    - $\Pi_{\text{city}}(\text{Branch}) - \Pi_{\text{city}}(\text{PropertyForRent})$
### 5.2.5 Intersection
- **$R \cap S$**
- Tuples in both R and S
- R and S must be union-compatible
- Derived from basics: **$R \cap S = R - (R - S)$**
- Ex. cities with both a branch office and at least one property for rent
    - $\Pi_{\text{city}}(\text{Branch}) \cap \Pi_{\text{city}}(\text{PropertyForRent})$
### 5.2.6 Cartesian Product
- **$R \times S$**
- Concatenation of _every_ tuple of R with _every_ tuple of S
- Ex. names and comments of clients who viewed a property
    - $(\Pi_{\text{clientNo, fName, lName}}(\text{Client})) \times (\Pi_{\text{clientNo, propertyNo, comment}}(\text{Viewing}))$
    - Result has lots of junk rows (mismatched clientNos)
- Fix: add a selection on matching keys
$\sigma_{\text{Client.clientNo = Viewing.clientNo}}\big((\Pi_{\text{clientNo, fName, lName}}(\text{Client})) \times (\Pi_{\text{clientNo, propertyNo, comment}}(\text{Viewing}))\big)$
- Cartesian product + Selection reduces to a single op, the **Join**
### 5.2.7 Join Operations
- **Join** is a derivative of Cartesian product
- Same as a Selection (using the join predicate) over the Cartesian product of the operands
- One of the hardest ops to implement efficiently in an RDBMS
    - One reason RDBMSs have intrinsic performance problems
- Forms of join:
    1. Theta join
    2. Equijoin
    3. Natural join
    4. Outer join
    5. Semijoin
#### 5.2.7.1 Theta join (θ-join)
- **$R \bowtie_F S$**
- Tuples satisfying predicate F from the Cartesian product of R and S
- F has form $R.a_i ;\theta; S.b_i$
    - θ is one of $<, \leq, >, \geq, =, \neq$
- Rewrite: **$R \bowtie_F S = \sigma_F(R \times S)$**
- **Degree** of a theta join = sum of degrees of the operands
    - $\text{degree}(R \bowtie S) = \text{degree}(R) + \text{degree}(S)$
    - Ex. R(a, b) has degree 2, S(c, d, e) has degree 3, so $R \bowtie_{R.a = S.c} S$ has degree 5 with attributes (a, b, c, d, e)
#### 5.2.7.2 Equijoin
- Theta join where predicate F has _only equality (=)_
- Ex. names and comments of clients who viewed a property
    - $(\Pi_{\text{clientNo, fName, lName}}(\text{Client})) \bowtie_{\text{Client.clientNo = Viewing.clientNo}} (\Pi_{\text{clientNo, propertyNo, comment}}(\text{Viewing}))$
- Result keeps _both_ copies of the common attribute
#### 5.2.7.3 Natural join
- **$R \bowtie S$**
- Equijoin of R and S over **all common attributes** x
- One occurrence of each common attribute is eliminated from the result
- $R \bowtie S = \Pi_{\text{without duplicate } x\text{'s}}(R \bowtie_{R.x = S.x} S)$
- Ex. same client/viewing query
    - $(\Pi_{\text{clientNo, fName, lName}}(\text{Client})) \bowtie (\Pi_{\text{clientNo, propertyNo, comment}}(\text{Viewing}))$
#### 5.2.7.4 Outer join
- Use to show rows that _don't_ have matching values in the join column
- **Left (natural) outer join** ($R ⟕ S$): keeps every tuple in the left relation
    - Unmatched tuples from R are padded with nulls for S's attributes
- **Right outer join** ($R ⟖ S$): keeps every tuple in the right relation
- **Full outer join** ($R ⟗ S$): keeps all tuples from both, padded with nulls where no match
- Ex. status report on property viewings
    - $\Pi_{\text{propertyNo, street, city}}(\text{PropertyForRent}) ⟕ \text{Viewing}$
    - Properties with no viewings still show up
#### 5.2.7.5 Semijoin (Semi-Theta join)
- **$R \ltimes_F S$**
- Tuples of R that _participate_ in the join of R with S
- Only R's attributes in the result
- Rewrite w/ projection and join: **$R \ltimes_F S = \Pi_A(R \bowtie_F S)$**
    - A is the set of all attributes of R
- Ex. complete details of all staff who work at the Glasgow branch
    - $\text{Staff} \ltimes_{\text{Staff.branchNo = Branch.branchNo}} (\sigma_{\text{city = 'Glasgow'}}(\text{Branch}))$
- Benefit: cuts down data that has to move/join, ex. in distributed setups
### 5.2.8 Rename
- **$\rho_S(E)$** or **$\rho_{S(a_1, a_2, \ldots, a_n)}(E)$**
- Gives expression E a new name S
- Optionally names the attributes $a_1, a_2, \ldots, a_n$
- Ex. (from GeeksforGeeks)
    - Rename attributes Name, Age of Department to A, B
    - Rename table Project to Pro and its attributes to P, Q, R
    - Rename first attribute of Student(A, B, C) to P
    - Rename relation Student to MaleStudent, and attributes RollNo, SName to (Sno, Name)
### 5.2.9 Division
- **$R \div S$**
- Relation over attributes C (the attributes in R but not S)
- Tuples from R that match the combination of _every_ tuple in S
- Derived from basics:
    1. $T_1 \leftarrow \Pi_C(R)$
    2. $T_2 \leftarrow \Pi_C((S \times T_1) - R)$
    3. $T \leftarrow T_1 - T_2$
- Think "for all" queries
- Ex. clients who have viewed _all_ properties with three rooms
    - $(\Pi_{\text{clientNo, propertyNo}}(\text{Viewing})) \div (\Pi_{\text{propertyNo}}(\sigma_{\text{rooms = 3}}(\text{PropertyForRent})))$
### 5.2.10 Aggregate Operations
- **$\mathfrak{I}_{AL}(R)$**
- Applies aggregate function list AL to R to define a relation over the aggregate list
- AL = one or more `(aggregate_function, attribute)` pairs
- Main aggregate functions: COUNT, SUM, AVG, MIN, MAX
- Ex. how many properties cost more than £350/month?
    - $\rho_{R(\text{myCount})}, \mathfrak{I}_{\text{COUNT propertyNo}}(\sigma_{\text{rent} > 350}(\text{PropertyForRent}))$
### 5.2.11 Grouping Operation
- **${}_{GA}\mathfrak{I}_{AL}(R)$**
- Groups tuples of R by grouping attributes GA, then applies AL
- Result has the grouping attributes GA _plus_ the result of each aggregate function
- Ex. number of staff in each branch and the sum of their salaries
    - $\rho_{R(\text{branchNo, myCount, mySum})}, {}_{\text{branchNo}}\mathfrak{I}_{\text{COUNT staffNo, SUM salary}}(\text{Staff})$
### 5.2.12 Symbol Summary

|Operation|Symbol|Notes|
|---|---|---|
|Selection|$\sigma$|rows (horizontal)|
|Projection|$\Pi$|columns (vertical), removes dupes|
|Union|$\cup$|union-compatible|
|Set difference|$-$|union-compatible|
|Intersection|$\cap$|R − (R − S)|
|Cartesian product|$\times$|all combos|
|Theta / Equi join|$\bowtie_F$|σ_F(R × S)|
|Natural join|$\bowtie$|common attrs, one copy kept|
|Outer join|⟕ ⟖ ⟗|left / right / full, nulls pad|
|Semijoin|$\ltimes$|R's attrs only|
|Rename|$\rho$|new relation/attr names|
|Division|$\div$|"for all"|
|Aggregate / Grouping|$\mathfrak{I}$|COUNT, SUM, AVG, MIN, MAX|

## 5.3 Relational Calculus
- Query specifies **what** to retrieve, not _how_
- No description of how to evaluate the query
- Based on first-order logic (predicate calculus)
    - **Predicate** is a truth-valued function w/ arguments
    - Substitute values for the arguments and you get a **proposition**, either true or false
- If a predicate has a variable (ex. 'x is a member of staff'), x needs a **range**
    - Some values in the range make the proposition true, others false
- Two forms: **tuple** and **domain**
- Logical connectives:
    - $\land$ (AND)
    - $\lor$ (OR)
    - $\sim$ (NOT)
### 5.3.1 Tuple Relational Calculus
- Find tuples for which a predicate is true
- Uses **tuple variables**
    - A variable that _ranges over_ a named relation, only permitted values are tuples of that relation
- Range of tuple variable S as the Staff relation: **$\text{Staff}(S)$**
- Set of all tuples S such that F(S) is true: **${S \mid F(S)}$**
    - F is a formula (_well-formed formula_, wff)
- Ex. details of all staff earning more than £10,000
    - ${S \mid \text{Staff}(S) \land S.\text{salary} > 10000}$
- Ex. just the salary attribute
    - ${S.\text{salary} \mid \text{Staff}(S) \land S.\text{salary} > 10000}$
### 5.3.2 Domain Relational Calculus
- Variables take values from **domains** instead of tuples of relations
- General expression: **${d_1, d_2, \ldots, d_n \mid F(d_1, d_2, \ldots, d_m)}$**
    - F is a formula built from atoms
    - $d_1, \ldots, d_n$ are domain variables
- Ex. names of all managers earning more than £25,000
    - ${fN, lN \mid (\exists sN, posn, sex, DOB, sal, bN),(\text{Staff}(sN, fN, lN, posn, sex, DOB, sal, bN) \land posn = \text{'Manager'} \land sal > 25000)}$
- Shorthand: $(\exists d_1, d_2, \ldots, d_n)$ in place of $(\exists d_1, \exists d_2, \ldots, \exists d_n)$
### 5.3.3 Equivalence and Safe Expressions
- An expression is **safe** if all values in the result come from the domain of the expression
- Safe domain relational calculus ≡ safe tuple relational calculus ≡ relational algebra
- So every relational algebra expression has an equivalent relational calculus expression, and vice versa
    - _This is why a language that matches them is "relationally complete"_
## 5.4 Other Languages
- **Transform-oriented** languages
    - Non-procedural, use relations to transform input data into required outputs
    - Ex. SQL
- **Graphical** languages
    - Show a picture of the relation's structure, user fills in an example of what's wanted, system returns data in that format
    - Ex. QBE
- **4GLs**
    - Build complete customized applications with a limited set of commands
    - User-friendly, often menu-driven
- **5GLs**
    - Some systems accept a form of natural language
    - Still at an early stage
## 5.5 References
- Relational algebra: http://en.wikipedia.org/wiki/Relational_algebra
- Relational Algebra Introduction: http://egorhm.net/relational%20algebra/programming/2014/05/10/relational-algebra-introduction.html
- GeeksforGeeks (rename examples, algebra vs calculus): https://www.geeksforgeeks.org/rename-operation-in-relational-algebra/
## Homework 2
a. $\Pi_{\text{equipNo, description, dailyRate}}(\sigma_{\text{category} = vision}(\text{Equipment}))$
b. $\Pi_{\text{firstName, lastName}}(\sigma_{(\text{year} \geq 3) \,\land\, (\text{program = Computing Science})}(\text{Student}))$
c. $\Pi_{\text{equipNo, description}}(\sigma_{\text{dailyRate} ≤ 18}(\text{Equipment}))$
d. $\Pi_{\text{studentNo, firstName, lastName, description}}\big((\text{Student} \bowtie \text{Loan}) \bowtie \text{Equipment}\big)$
e. $\Pi_{\text{equipNo, description, firstName, lastName}}\big(\text{Equipment} ⟕ (\sigma_{\text{dateReturned = NULL}}(\text{Loan}) \bowtie \text{Student})\big)$
f. $\Pi_{\text{studentNo}}\big(\text{Loan})$
g. $\Pi_{\text{studentNo, equipNo}}(\text{Loan}) \div \Pi_{\text{equipNo}}(\sigma_{\text{category = VR}}(\text{Equipment}))$


