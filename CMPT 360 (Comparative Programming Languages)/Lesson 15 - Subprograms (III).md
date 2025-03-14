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
- 