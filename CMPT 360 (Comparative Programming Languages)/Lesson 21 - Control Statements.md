#complete
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
- Rules
	- Cases of the switch value must be integer valued:
	- Listed individually
	- Each section needs a break to conclude - a *goto* the end
- Modula-2 has:
```modula-2
CASE digit OF
	0:
		statements |
	1,3,4:
		statements |
	5..9:
		statements
	ELSE
		statements
	END;
```
- Rules
	- Ranges and lists are allowed
	- | serves to separate cases in classic, ISO
	- | comes before each case in R-10
	- No break is needed
- Pascal is similar to Modula-2 except only some versions had *OTHERWISE*. The rest either:
	- Throw a run time error if no case is selected
	- OR require every case possible to be listed
- Ada has:
```ada
case THINGY of
	when selection1 --> statement1
	when selection2 --> statement2
	...
	when others --> statmentn+1
end case
```
###### Notes
1. Overlaps among selected cases are not permitted.
2. What can the selector be?
	- In ALGOL 68 an integer.
	- From Pascal on, an ordinal type.
3. There are other variations on the selection as well.
### Repetition
- **Note** that some call these all iteration, but that is much too specific.
##### Counting Loops or iterations
- Fortran has the Do Loop
	- **Note1**: All such loops are guarded by the counter value.
	- **Note2**: Variation on this theme are found in most languages as *for* loops
- Pascal could count up or down on any scalar by 1.
```
for month = Jan to Dec do
	...
end
for count = 10 downto 0 do
	...
end
```
- C has `for (expression1; expression2; expression3)`
	- Where expression1 is assignment (e.g. counter = 0)
	- expression2 is test (e.g. counter < 10)
	- expression3 is modification (e.g. counter++)
- C++ uses the same syntax as C but:
	- The expressions may be complex
	- The variable could be changed in the loop and the test would be re-evaluated.
- Several other languages use this syntax; rules vary.
- Modula-2 (Classic & R10)
```
FOR count := startValue TO stopValue by ∆ DO
	statementSequence
END
```
- Modern languages
```
FOR variable IN values Do
	statements
END
```
- Where the iteration depends on the type and must be defined elsewhere.
##### Notes
- Rules for FOR loops *may* include some or all of:
	- The counter may not be threatened with change in the loop.
	- The counter value is undefined outside the loop
	- Mentioning the counter in the header is the declaration and opens a scope for a new entity
	- Only integer counters allowed
	- Counter parameters for start, and evaluated *once*
