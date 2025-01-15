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
## Java Package Implementation
- Below is an example of implementing the StackADT interface.
```java
package jsjf;
/**
* Defines the interface to a stack collection.
*
* @author Java Foundations
* @version 4.0
*/
public interface StackADT<T>
	{
	/**
	* Adds the specified element to the top of this stack.
	* @param element element to be pushed onto the stack
	*/
	public void push(T element);
	/**
	* Removes and returns the top element from this stack.
	* @return the element removed from the stack
	*/
	public T pop();
	/**
	* Returns without removing the top element of this stack.
	* @return the element on top of the stack
	*/
	public T peek();
	/**
	* Returns true if this stack contains no elements.
	* @return true if the stack is empty
	*/
	public boolean isEmpty();
	/**
	* Returns the number of elements in this stack.
	* @return the number of elements in the stack
	*/
	public int size();
	/**
	* Returns a string representation of this stack.
	* @return a string representation of the stack
	*/
	public String toString();
}
```
- Exception Handling
```java
/**
* Removes the element at the top of this stack and returns a
* reference to it.
* @return element removed from top of stack
* @throws EmptyCollectionException if stack is empty
*/
public T pop() throws EmptyCollectionException
	{
	if (isEmpty())
		throw new EmptyCollectionException("stack");
		
	top--;
	T result = stack[top];
	stack[top] = null;
	
	return result;
}
/**
* Returns a reference to the element at the top of this stack.
* The element is not removed from the stack.
* @return element on top of stack
* @throws EmptyCollectionException if stack is empty
*/
public T peek() throws EmptyCollectionException
{
	if (isEmpty())
		throw new EmptyCollectionException("stack");
		
	return stack[top-1];
}
/**
* Represents the situation in which a collection is empty.
*
* @author Java Foundations
* @version 4.0
*/

public class EmptyCollectionException extends RuntimeException
{
	/**
	* Sets up this exception with an appropriate message.
	* @param collection the name of the collection
	*/
	public EmptyCollectionException(String collection)
	{
		super("The " + collection + " is empty.");
	}
}
```