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
- If we were to define a stack that holds object references, then it could hold any object.
	- However, this means control over type of element added is lost.
- A better solution to define a class is by using a *generic type*.
- The generic placeholder is is specified in angle brackets in the class header:
```java
class Box<T>
{
	//declarations and code that refer to T
}
```
- Any identifier can be used, but T (for Type) or E (Element) have become standard practice.
- Then, when a `Box` is needed, it is instantiated with a specific class instead of T:
	- `Box<Widget> box1 = new Box<Widget>();`
- Now, `Box1` can only hold `Widget` objects.
	- The compiler will issue errors if we try to add a non-widget to the box.
- Using the same class, another object can by instantiated.
	- `Box<Gadget> box2 = new Box<Gadget>();`
- Generics such as these provide better type management control, and simplify use of collections.
## Postfix Expressions
- These use the stack collection to eliminate the need for traditional order of operations.
	- **Infix**: `(3 * 4 – (2 + 5)) * 4 / 2`
	- **Postfix**: `3 4 * 2 5 + – 4 * 2 /`
- To evaluate, scan left to right.
	- If an operand (value) is encountered, push it onto the stack.
	- If an operator is encountered, pop the top two elements, operate, and push the result.
![[Pasted image 20241212094711.png]]

