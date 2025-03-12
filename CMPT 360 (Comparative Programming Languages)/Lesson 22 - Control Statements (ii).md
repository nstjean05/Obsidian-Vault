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


**22.  _Control Structures (2)_**

**[3]** a. Should C's single operand assignments such as ++int and int-- be allowed in other languages? Why or why not?
- I think that they should certainly be allowed in other languages. These single operand assignments offer an effective and simple way to increment and decrement a counter. They are highly useful in iterative loops, and for keeping track of any number of metrics. Additionally, they can increase the speed of the program by condensing what may be multiple operations into a single operation.
https://www.geeksforgeeks.org/operators-in-c/

**[3]** b. Should an optimizing compiler for C or C++ be allowed to change the order of evaluation of Boolean expressions? Why or why not? What about Modula-2?
- I do not think that this would be a good idea for C(++), as changing truth-values can have cascading side effects, such as modifying variables. Additionally, if the order of evaluation of a program is changed, then when the boolean is collected it may take on the wrong value. Optimizing compilers are not inherently detrimental, but in this specific case are not worth the potential side-effects. This would not impact Modula-2 as strongly, as it is more strict in its evaluation of a boolean expression.
https://arjaybooks.com/Modula-2/Text/Ch3/Ch3.3.html

**[3]** c. Why does Java specify that operands in expressions must be evaluated left to right?
- The primary reason for this evaluation is to keep the program predictable and readable. In languages such as English, this same format is kept, so it follows that this lo