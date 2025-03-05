










**12.**  **_Type Checking, Scope_** 

**[3]** a. Write a code snippet to illustrate that the scope of a variable may not extend to an enclosed function or procedure.
```java
//Java
public class Adding {
	public static void main(String[] args) {
		int x = 1;
		int result = addOne(x);
		System.out.println("1 + 1 = " + result);
	}
	public static int addOne(int number) {
		int result = number + x;
		//int result = number + 1;
		return result;
	}
}
```

**[3]** b. Suppose you write a function or procedure with parameters and local variables in your favourite language (name it so I know what you are talking about!) What is the scope of (i) the name of the procedure (ii) the procedure parameters (iii) the procedure/function's local variables? (Languages vary in this respect.)

