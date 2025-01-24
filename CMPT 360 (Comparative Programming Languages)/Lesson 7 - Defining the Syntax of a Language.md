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
- For valid communications, much is missing from these sentences.
	- Contextual capitalization
	- Articles
	- Singular/plural noun and verb forms
	- Meaning: a valid sentence per the rules may be nonsense. This is true of computer programs also.
#### More Vocabulary
1. Each string being used (sentence/noun/verb) is called a sentential form.
2. Each thing needing/being defined (left side) is a non-terminal
3. Each right-side item with no further definition is called a terminal
4. Each rule is a production
5. Here, the start-symbol or base is `<sentence>`
6. In computing, valid programs are sentences (usually also ending with a period) and the start symbol may be `<program>`, `<module>`, `<package>`, or something similar.
#### Definition _3_
- An extended BNF or EBNF has two more rules that do not add 