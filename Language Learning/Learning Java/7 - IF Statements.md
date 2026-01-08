- An `if` statement executes a code block given that its condition is true.
- The `if` is the first statement, entering the program into the tree.
	- `else if` allows for subsequent qualifications.
	- `else` is a catch-all for any condition that is not already met.
- Note that only the first valid (in line-order) statement will be executed, and the rest skipped.
```java
int age = 25;

if (age >= 18){
	System.out.println("You're an adult.")
}
else if (age < 0){
	System.out.println("You don't exist yet!")
}
else if (age == 0){
	System.out.println("You are a baby")
}
else{
	 System.out.println("Your're a child.")
}
```