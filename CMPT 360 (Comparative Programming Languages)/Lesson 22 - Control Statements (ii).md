## Control Statements Contd.
### Condition or Logic Driven Loops
```java
while condition do
	statements
end

repeat
	statements
until condition

do
	statements
while condition
```
- The logic is different for each of the above
- C allows "continue" to skip following statements
- C# has `break <label>` to escape from an inner loop and end a labelled loop
##### Variations
```java
do while condition
	statements
od

do until condition
	statements
od
```
- Some languages may have `EXIT` statements either to terminate...
	- the current (in the nested sense) loop
	- a particular kind of loop
	- a named loop with `EXIT<label>` like C# break
### Indefinite Loops
- Modula-2:
```modula2
Loop
	statement sequence
	IF condition THEN EXIT END
	statement sequence
END
```
- Ada:
```ada
[label] loop
	statement sequence
	exit[label] when condition
	statement sequence
end loop
```
### Combinations
- PL/1 and ALGOL have
	- `(for i from j by k to m) while b do .. od`
	- One can omit:
		- The for clause
		- The while clause
		- the from and by point (and then are = 1)
			- e.g. `to 15 do a := a + 3 od`
				- would add 45 to a