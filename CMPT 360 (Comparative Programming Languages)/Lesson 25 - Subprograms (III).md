#complete 
### What can a function return?
- Usually any built-in type can be a return type.
- The type matching rule for a return value is *usually* the same as for assignment.
- *Some* languages prohibit structured types, or even all user defined types from being return types, though C allows pointers as returns
- Even if structured types are allowed, they must be names, not anonymous.
	- `PROCEDURE DoIT(VAR p:REAL):ARRAY10 OF REAL`
- In most languages, a pure function (i.e. with a return value) should *not* also have reference parameters that are writable. This is a side-effect that as a previous example showed, could cause such things as commutativity to fail.
- C++, Modula-2, and Ada allow anything to be returned.
- Access to global variables may be restricted, or may require syntax such as COMMON or EQUIVALENCE.
- User defined operator overloading may be permitted using functions.
### Overloaded Subprograms
- These are two or more procedures/functions with the same name, but different structures.
	- `PROCEDURE DoIT(VAR n:INTEGER)
	- `PROCEDURE DoIT(VAR n,m:INTGER)
	- If you call `DoIT` with one parameter, it will give you the first procedure, and if you call it with two parameters, then it will run the second procedure.
- Used in languages such as C++ and Ada
- Such overloading is common in OO languages where the methods of an object class may be overloadable in this way.
### Generic Subprograms
- These are polymorphic and their definitions take parameters that describe their signatures.
- In C++ this is done with a function template that is refined when the function is named in a call.
```C++
//example in C++
include <iostream>
using std: cout;
using std: endl;

//Function template to print out an array
template <typename TN>
void outputArray(const TN * const array, int size)
{
	for (int count = 0; count < size; count++)
		cout << array[count] << " ";
	cout << endl;
} //end of function template outputArray

int main()
{
	const int Asize = 4;
	const int Bsize = 3;
	int A [Asize] = {4,-3,2,5}
	float B [Bsize] = {3.9, 2.4, 7.7}
	cout << "The array A holds:" << " ";
	outputArray (A,Asize);
	cout << "The array B holds: " << " ";
	outputArray (B, Bsize);
	return 0;
	//end main
}
```
- The above would yield:
	- The array A holds: 4 -3 2 5
	- The array B holds: 3.9 2.4 -1.7
- And we could also use this to print other arrays, such as an array of characters.
- Java has generic methods in 5.0 and up.
- Ada has, for instance:
```Ada
generic
	type ITEM is private;
	procedure swap (x,y: in out ITEM) is
		temp:ITEM=x;
		begin
			x:=y;
			y:=temp;
		end swap;
```
- But before use, the generic procedure must be refined for a specific data type, this procedure realSwap is new swap (float)
	- And only then may use in code realSwap(r1, s2)
- Ada also permits operations in parameters.
### Variables of Type "TYPE"
- Modula-2 has some procedures that take implicit parameters of type TYPE, but these are only in the base langauge; users cannot write them.
	- e.g. `VAL(INTEGER, n)` or `MAX(CARDINAL)`
- In Russell variables can be of type TYPE
- In Modula-2 one can write a generic swap using parameters ARRAY OF SYSTEM.LOC (but this breaks type checking entirely)
- In Modula-2 ISO one cannot write generic procedures on their own but can create generic modules that are parameterized for types that their procedures can then use.
### Compilation of Program Units
- Such as library modules, packages, etc. may be:
#### Independent
- Compilation without reference to other units
	- No cross checking of parameter types, say, between a program and a library unit or between two library units.
#### Separate
- Perhaps done at different types but with a strategy to cross-check interfaces and enforce consistency.
##### Typical
- All interface units are compiled first.
- Then the program can be compiled as only syntax need be checked and the interface has this.
- Of course, before anything can be linked, all the implementations (code) must also be compiled and checked for consistency with the interfaces.


**25. W** **Mar 17** **_Subprograms (3); Issues with functions, Overloading, Generics_** 

**[3]** a. The Ada standard says that implementors can choose to implement inout (not in out) parameters either with copy semantics or with reference semantics. Is this a good thing? Argue your position.
- Copy semantics refer to copying the value rather than the pointer of a variable, and reference semantics do the opposite. `inout` is the mode in which parameters can receive data from and return data its calling function. I think that this is a good thing, as it allows the program to be more specifically optimized. Giving programmers the choice between copy and reference semantics allows them to switch the two for different use cases, even within the same program.
Textbook

**[6]** b. Consider the following program written in C syntax:
```C
void swap (int a, int b)
{  int temp;
    temp = a;
    a = b;
    b = temp;
}

void main ()
{   int value = 2, list [5] = { 1, 3, 5, 7, 9 };
     swap (value, list [0]);
     swap (list[0], list [1]);
     swap (value, list[value]);
}
```
For each of the parameter passing methods : value, reference, value-result (look this one up), what will be the final values of the variables value and list when the code finishes?  
1. Value
	1. value = 2
	2. list = {1,3,5,7,9}
2. Reference
	1. value = 2
	2. list = {3,1,5,7,9}
3. Value-Result
	1. value = 2
	2. list = {3,1,5,7,9}

**[5]** c. Write a program in your favourite language that demonstrates different results can be had if parameter passing semantics is by value or by reference. (Same code for both except for the parameter). Run your code and show me what the output actually was in each case.
