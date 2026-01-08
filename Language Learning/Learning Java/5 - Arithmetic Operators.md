#### Simple Operators
- There operators are used to do math in programming.
```java
int x = 10
int y = 2
int z;
```
- Addition
	- z = x + y;
	- x +=y ;
- Subtraction
	- z = z - y;
	- x -= y;
- Multiplication
	- z = z * y
	- z *= y;
 - Division
	- z = z / y;
	- z /= y;
- Modulus
	- z = z % y;
	- z %= y;
	- **Note**: Modulus display the remainder of $z/y$.
- Pay attention to the variable type you are using while performing operations.
	- For example, dividing integers 1 by 2 would not equal 0.5, but would round up to 1.
	- Make sure to use float or otherwise in this case.
#### **Increment and Decrement Operators**
```java
//Set variable x equal to 1
int x = 1;

//Increment x by more than 1
x = x + 2;
x += 2;

//Increment by 1
x++;
```
- The above are the same for decrementing, simply substitute the *+* sign for a *-* sign.
#### PEMDAS
- Use PEDMAS to correctly order your arithmetic operations.
```java
double result = 3 + 4 * (7 - 5) / 2.0

// = 3 + 4 * (2) / 2
// = 3 + 4 * 1
// = 3 + 4
// = 7
//Outputs 7.0
```