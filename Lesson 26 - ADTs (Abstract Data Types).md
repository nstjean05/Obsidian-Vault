#incomplete 
### ADTs
- **Abstraction** is a (high level) view or representation of an entity or process that obscures (deliberately hides) all but the ideas of significant interest.
	- e.g. Subprograms are process abstractions
	- e.g. Modules/Packages are encapsulation abstraction
- Different people employ different levels of abstraction.
	- e.g. An automobile looks different to...
		- Designer
		- Engineering Team
		- Assembly Line Mechanics
		- Clerks ordering parts
		- Drivers
		- Passengers
	- A computer program is likewise. The designer, programmer, and user all have different views.
	- e.g. A skill like riding a bicycle must be abstracted to the point where you do it instinctively. If you stop to think about details, you fall over.
### Built-In Data Types
- Such as float, int, CARDINAL, BOOLEAN are abstract, for they include:
	- A range of values
	- All permitted operations
	- No information on their internal structure or storage is normally available to the program unless specified in the language definition, and even then low-level (unsafe) functions provide the only access to these.
- The essence is...
	- encapsulation
	- data hiding
### User-Defined ADTs
- Some languages have more (better) facilities than others.
- Goals:
	- Modifiability (depends on implementation)
	- Reusability (standard reusable interface)
	- Security (protection from modification by other units)
- Implementation requires...
	- An encapsulation abstraction mechanism such as classes, modules, and packages.
	- Also nice are...
	- Information hiding via an interface
	- Generics?
### ADT Example 1
- First, define the ADT, its properties and all operations:

|                          | Complex    | Vector      | Point            |
| ------------------------ | ---------- | ----------- | ---------------- |
| Properties               | For all 3, | a pair of   | real coordinates |
| Operations:              |            |             |                  |
| Create                   | Yes        | Yes         | Yes              |
| Destroy                  | Yes        | Yes         | Yes              |
| Construct                | Yes        | Yes         | Yes              |
| Parts (inspectors)       | Re, Im     | Rise, Run   | Projections      |
| Alternate Representation | abs, ary   | length, ary | x                |
| Operators                | + - * /    | + - * neg   | reflect          |
