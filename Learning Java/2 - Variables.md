- A variable is a reusable container for a value.
	- It behaves as if it is the value is contains.
## Two Variable Types
- **Primitive:**
	- A value which is stored directly in memory (stack)
	- *int*, *double*, *char*, *boolean* fall under this type.
- **Reference:**
	- A memory address (stack) which points to the (heap)
	- It is a pointer to the actual value.
	- *string*, *array*, *object* fall under this type.
## Declaring Variables
- Two steps:
	1. Declaration
	2. Assignment
```java
//Declaration: Create the variable (int counter)
//Assignment: Give it a value (counter = 1)
int counter = 1;

double price = 2.5;
double value = -13.88;

char grade = 'A';
char symbol = '!';

boolean isCoder = true;
boolean touchesGrass = false;

System.out.println("The counter is " + counter + ".");

//Displays the 'if' statement when true
if(isCoder){
	System.out.println("You're a coder.");
	}
else{
	System.out.println("You are not a coder.");
	
	}
	
String hockeyTeam = "Vancouver Canucks";
System.out.println("The best team is the " + hockeyTeam + symbol);

/*
Output:
The counter is 1
You're a coder.
The best team is the Vancouver Canucks!
*\
```

