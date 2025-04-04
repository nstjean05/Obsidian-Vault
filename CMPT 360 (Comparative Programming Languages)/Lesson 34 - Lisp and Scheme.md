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
	;Returns A, the first element in the list (head)
CAR = "Contents of the address register"
```
- Note in each of the above, A or D can be repeated
```LISP
;e.g
CAR(CDR(L)) = CADR(L)
CDDR(QUOTE(A B C)) returns(C)
CADR(QUOTE(A B C)) returns B
```
- Type 4:
	- CONS
	- Tacks a new head on a list
	- `(CONS(QUOTE(A) QUOTE(B C))` --> `(A B C)`
- Type 5:
	- Boolean functions return the atom T if true and the atom NIL if false
```LISP
;ATOM? returns T if its argument is an atom
(ATOM?('x)) ; --> T
;but
(ATOM?('(x))) ; --> NIL
;A last is not an atom

;NUL? returns T if its argument is empty
(NUL?('())) ; --> T

;EQ? returns T if its two arguments are the same
(EQ?('(x)) ('(x))) ; --> T

;Member? returns T if its first argument is a member of its second
((member? ('B) ('(A B C D)))) ; --> T
```