#complete 
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

|                          | Complex    | Vector        | Point                      |
| ------------------------ | ---------- | ------------- | -------------------------- |
| Properties               | For all 3, | a pair of     | real coordinates           |
| Operations:              |            |               |                            |
| Create                   | Yes        | Yes           | Yes                        |
| Destroy                  | Yes        | Yes           | Yes                        |
| Construct                | Yes        | Yes           | Yes                        |
| Parts (inspectors)       | Re, Im     | Rise, Run     | Projections                |
| Alternate Representation | abs, ary   | length, ary   | x                          |
| Operators                | + - * /    | + - * ⊗ ⊙ neg | translate, rotate, reflect |
- All three use a pair of float/real but they are not the same
- All three depend on float/real operations and properties
	- e.g. commutativity, etc.
- Another library may contain subsidiary operations as relevant, such as forComplex trig, log, exp, etc.
### ADT Example 2
- Aggregate organization structures can be ADTs as well.
	- Such as stack, queue, binary tree, heap, B-tree, etc.

|                        | Queue (FIFO)        | Stack (LIFO) | Binary Tree      |
| ---------------------- | ------------------- | ------------ | ---------------- |
| **Construct (Create)** | Create              | Create       | Create           |
| **Destruct (Destroy)** | Destroy             | Destroy      | Destroy          |
| **Incorporate**        | Enqueue             | Push         | enTree           |
| **Inspect**            | Next                | Peek         |                  |
| **Inspect (contd.)**   | Full/Empty          | Full/Empty   | Empty            |
| **Remove**             | Dequeue             | Pop          | deTree           |
| **Locate**             | isQueued            | isStacked    | find             |
| **Process**            | Iteratively remove- | -and process | Traverse/process |
- Once the ADT is defined, it must be implemented
- C#, C++ encapsulates using a namespace.
	- Libraries outside the namespace have their entities qualified for use inside.
	- This is similar to a module, though the semantics are different.
- In Modula-2 (ISO) `COMPLEX` is built in as an ADT
	- Variables of this type (and `LONGCOMPLEX`) need only be declared. (`+-*/` are overloaded)
	- The constructor is `CMPLX(a,b)` and the inspectors are `RE` and `IM`
	- All other functions are in the library ComplexMath
- In Modula-2 as previously noted, other ADTs are best implemented in a library module, which has two points.
- Java has packages, which is one compilation unit (not like Modula-2)
	- In two parts:
		- Package specification (interface/definition)
		- Package body
	- In the specification, the structural details of a type are provided but may be designated private and therefor inaccessible to client code.
- In Euclid, modules are types


**26.** **_Start ADTs Modules and their ilk_**

**[6]** a. Write sample code to show that having a function modify reference parameters can return different results than if the same code is written with value parameters. Run this and hand in the output to show you have indeed answered the question. Give a fundamentally different example than the answer you gave for number 25c.

  
**[4]** b. What restrictions, if any, are there on function return types in (a) Java and (b) Python


**[6]** c. Class types, whose entities are objects are one kind of ADT. Describe how class types are written in Objective-C or ISO Modula-2 (with object extensions) or Java and say how this differs from implementing ADTs in a library (if it does in all cases).


**[3]** d. Some software engineers believe that imported entities should always be fully qualified with the name of the container (exporting program unit). Do you agree? Support your argument.


**[3]** e. Comment on the use of destructors in C++ and Java.

