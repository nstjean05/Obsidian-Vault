#computer-science 
## Collection Terminology
- A *collection* is an object that holds and organizes other objects.
	- They provide operations for accessing and managing those elements.
	- Many standardized collections have been defined over time.
- Some collections are *linear* in nature, whereas others are *non-linear*.
	- **Linear:** Each element links to one more element, and has one element linked to it.
	- **Non-Linear**: Elements may link to more than one element.
	- Left: Linear, Right: Non-Linear

![[Pasted image 20241212091311.png]]

## Abstractions
- An abstraction hides details to make a concept easier to manage.
- All objects can be considered as abstractions, as they use an interface.
- This means that objects are generally great mechanisms for implementing collections.
###### Abstract Data Type
- A *data type* is a group of values and the operations defined on those values.
- An *abstract data type (ADT)* is a data type that isn't pre-defined in the language.
- A *data structure* is the set of programming constructs and techniques used to implement a collection.
- Sometimes the differences between these three ideas are blurred.
###### The Java Collections API
- The classes provided within Java are called the *Java Application Programming Interface* (API).
	- Those classes which support collections are called the *Java Collections API*.
## Stacks
- A **stack** is a linear collection whose elements are added last in, first out (LIFO).
	- That is, the last element added to the stack is the first one to be removed.
	- Adding and removing elements is done from the top.
###### Stack Operations
- push - Adds an element to the top of the stack.
- pop - Removes an element from the top of the stack.
- peek - Examines the element at the top of the stack.
- isEmpty - Determines if the stack is empty.
- size - Determines the number of elements stacked.
## Object-Oriented Concepts
- An *abstract method* is a method that doesn't have an implementation.
- An *interface* is a collection of constants and abstract methods.
- A class implements an interface by providing method implementations for each of the abstract methods defined in the interface.
- A *Polymorphic* reference is a reference variable that can refer to different types of objects at different points in time.
## Generics
- 