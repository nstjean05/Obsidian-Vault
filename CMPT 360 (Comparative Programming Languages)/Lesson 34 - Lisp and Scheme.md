#incomplete 
### Some LISP/Scheme
- Pure LISP (John McCarthy c. 1960) is purely functional, but there are more recent versions with other features.
- LISP --> List Processing Language
#### Objects
- Are either:
	- Atoms
		- Strings of characters representing a stored value
	- Lists
```LISP
;Atoms:
INTEREST
HELLO
65535

;Lists:
(MON TUE WED)
(5 6 9)
() = NIL; the empty list
;A program is a list
```
#### Notation
- Is a prefix
	- e.g. (PLUS x y)
#### Functions
- Type 1:
	a) QUOTE (A)
		returns A
	b) LIST(2)
		makes 2 into a list
- Type 2:
```LISP
(CAR(QUOTE(A B C)))
	;Returns A, the first element
```