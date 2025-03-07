#complete
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
	- Just do..od is like the Modula-2/Ada loop and requires an explicit leave to exit.
	- The control variable "c" even if explicit is local.
	- In ALGOL the expressions are evaluated on every iteration and can be real.
	- In Modula-2  R10 the `FOR` loop control can be `REAL`
- Ada has a decorated `loop` structure for all purposes
	- `iteration spec loop // body of loop // end loop`
	- Where iteration spec can be:
		- `while <condition>`
		- `for counter in <scalar range> in reverse <scalar range>`
	- and the loop body may contain
		- `exit (when <condition>)`
	- and loops can be named and exited by name.
##### General Notes
1. Loop control variables may be...
	- Declared in the loop or outside it
	- Modifiable (or not) in the loop body
	- Entirely local and implicit
2. All such control statements
	- Are abstractions for machine language jumps
	- Are problem oriented
	- Are able to eliminate obscurity in code
	- Can greatly improve efficiency
	- If minimized greatly reduce expressive power
### Other Kinds of Control
- Some languages have `GOTO <line number> | <label>` possibly with some restrictions
- Others use...
	- Break, leave, or EXIT to exit one or more kinds of loop
	- RETURN to exit a procedure
	- RETURN value to exit a function (required)
	- HALT to exit a program (normal termination)
	- RAISE or throw to go into exceptional execution mode
	- RETRY to exit exceptional execution mode and re-try the block from the start
- But all transfers of control should be used sparingly and in a controlled manner.
	- GOTO should be avoided altogether even if available as such undisciplined transfer leads to code that is hard to read and impossible to maintain.
### Iterations Based on Data Structures
- LISP `delist` operates on a list, automatically iterating through it.
- PYTHON has:
	- `for loop variable in object // loop body // else // else clause`
	- Where `object` is typically a range or a list
- Perl has:
	- `foreach $item (@itemArray) // (loop body)` Iterates like LISP doList
- C, C++, Java
	- Allow traversals to be done with a for loop
	- `for (p=rootPointer; p== null; traverse(p)) // body`
	- Where the traverse procedure concludes by resetting the reference parameter to point to the next logical node.
- Modula-2
	- Allows recursion in a procedure type definition
	- `TYPE TraverseProc = PROCEDURE (VAR node:NodeType VARP: TraverseProc)
	- `VAR Traverse:TraverseProc
	- "Traverse" is its own iterator and can set the next node to process and the next procedure to do so (exchange itself)
	- Just write Traverse(root, Traverse)
	- This is how you write a FiniteStateMachine.
		- Each node and current TraverseProc is a state and makes a transition.