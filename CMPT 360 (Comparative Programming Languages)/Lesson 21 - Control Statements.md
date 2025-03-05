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
		2. IF a closing market for an if is introduced, the problem goes away and the code becomes easier to understand.
			- Close markers in Algol 68 were the opening marker, spelled backwards.
			- Ada uses END if.
- Fortran had a multiple IF
```fortran
IF (expression) 10, 20, 30
10
	GOTO 40
20
	GOTO 40
30
	...
40
	...
```
- Some notations use IF to return values.
	- Algol: `a = if b then <expression1 else <expression2> fi`
- PL/1 had:
```pl/1
SELECT
	WHEN b1 statement1;
	WHEN b2 statement2;
	...
	OTHERWISE statementn+1
END;
```
- C has:
```C
switch (x-1)
{case 0:
	 statements
	 break;
case 1:
	 statements
	 break
	 ...
default
	statements
}
```
- Rules: Cases of the switch value must be interge