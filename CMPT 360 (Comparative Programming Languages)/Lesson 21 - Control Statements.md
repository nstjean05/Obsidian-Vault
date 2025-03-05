*Note: Lesson 20 does not exist*
## Control Statements
- The statement level control statements are:
### Sequencing
- Defines the order of statement execution
- Older languages use line numbers to sequence
- Modern ones sequence in the textual order.
### Selection
- FORTRAN had just: `IF expression THEN statement`
- ALGOL had `IF b then ...; ELSE begin ... end;`
	- The above two are called *guarded statements*, with the condition being the guard.
- Pascal and Java 
	```java
IF a THEN
	IF b THEN statementSequence1;
ELSE
	statementSequence2;
	```
	- But, this is ambiguous to the reader, for it could mean statementSequence2 is executed...
		1. When a is false (else applies to first *if*)
		2. When a is true and b is false (applies to second if)
	- So this has to be disambiguated in one of two ways:
		1. ALGOL, PL/1, Java, C++, and Pascal have a semantic rule that *else* belongs to the nearest (nested) *if*, hence interpretation (case 2) applies.
			- 
		2. 