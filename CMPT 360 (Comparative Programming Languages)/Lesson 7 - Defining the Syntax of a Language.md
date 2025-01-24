## Formally Defining
- The rules for doing this are themselves written in a notation
#### Definition _1
- A language used to describe the rules of a language (i.e its lexis, syntax, grammar) is a **metalanguage** and its symbols are **metasymbols**.
#### Definition _2
- A Backus-Naur-Formalism (BNF) (which is about the same as a linguist's Chomsky context free grammar) is based on.
1. A rule of succession or sequence.
	- e.g.    C = PQ    means Consists of P followed by Q
2. A rule of selection
	- e.g.    C = P | Q   means Consists of P or Q
3. The metasymbols
	- < >   to enclose the item defined
	- ::=    denotes "is described by"
	- "  "   enclosures literals
	- (  )    for grouping
		- e.g. `<sentence> ::= <noun> <verb> <noun> "."`
		-  `<noun> ::= "cat" | "boy" | "door| "tuba"`
		-  `<verb> ::= "eats" | "climbs" | "reads" | "sounds"`
	- According to these rules, "Cat reads tuba" is a valid sentence.
	- As long as the sentence follows the given form it is correct, regardless of whether it makes sense.