#complete
## Formally Defining
- The rules for doing this are themselves written in a notation
#### Definition _1
- A language used to describe the rules of a language (i.e its lexis, syntax, grammar) is a **metalanguage** and its symbols are **metasymbols**.
#### Definition _2
- A Backus-Naur-Formalism (BNF) (which is about the same as a linguist's Chomsky context free grammar) is based on.
1. A rule of succession or sequence.
	- `C = PQ`
	- Meaning C consists of P followed by Q
1. A rule of selection
	- `C = P | Q`
	- MeaingC consists of P or Q
1. The metasymbols
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
- Each string being used (sentence/noun/verb) is called a sentential form.
- Each thing needing/being defined (left side) is a non-terminal
- Each right-side item with no further definition is called a terminal
- Each rule is a production
- Here, the start-symbol or base is `<sentence>`
- In computing, valid programs are sentences (usually also ending with a period) and the start symbol may be `<program>`, `<module>`, `<package>`, or something similar.
#### Definition _3_
- An extended BNF or EBNF has two more rules that do not add additional meaning to a language, but do make it easier to write.
4. A rule of option
	- `C = [P]` or `C = P?`
	- Meaning C consists of P or nothing at all.
5. A rule of repetition
	- `C = {P}` (ISO) or `C = P* (R10)`
	- Meaning zero or more instances of P
#### Variations that may be used in some EBNFs
- All terminals quoted or no terminals quoted
- The metasymbols < > may be left out
- ::= may be shortened to `::` or `-->`
- Terminals may be separated 'by commas' (or not)
- Productions may be terminated by semicolons.
- Thus, Pascal was defined using a "busy" version of BNF
	- `<program> ::= <program-heading> ";" <program block> "."`
	- `<program-heading> ::= program <identifier> ["("Program Perameters")"]`
- The text uses
	- `<program> --> begin <stmt-list> end`
- The ISO Modula-2 standard used
```pascal
//Modula-2
compilation module = program module | definition module | implementation module
program module = "MODULE", moduleidentifier, [protection], semicolon, import lists, module block, module verification, period;
module identifier = identifier;
protection = left bracket, protection expression, right bracket;
protection expression = constant expression
semicolon = ";";
```
#### Final Observations
1. The EBNF rule of option
	- `C = [Q]` could be written in BNF as:
	- `C = Q|ε` provided there was a metasymbol `ε` for the empty string
2. Recursion is permitted in productions, so one could define:
	- Text Style:
		- `<identifier List> --> identifier|identifier, identifier List`
	- Comment Style:
		- `identifier List = Identifier{comma, identifier}`
	- Identifier List:
		- `identifier(comma, identifier)*`



 
**7. W _EBNF_**

**[6]** a.  How does the EBNF for the FOR loop differ between ISO and R10 Modula-2? For ISO see _http://www.arjaybooks.com/Modula-2/Text/index.html_ and appendices 2-3. For R10 see _https://github.com/m2sf/M2-R10-Syntax-Diagrams_

**[10]** b. Write EBNF descriptions for the following:

- a Java class definition header

- a Java method call statement

- a C switch statement

- a C union definition

- C float literals