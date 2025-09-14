- We use the keyword 'scanner' to take user input.
- Make sure to include `import java.util.Scanner` 
	- Includes the *util* package and *scanner* class
```java
//Create an object (scanner) of the Scanner class

Scanner scanner = new Scanner(System.in);

System.out.print("Enter your name: ");

//Creats a string "name", and assigns the user input to it.
String name = scanner.nextLine();

System.out.println("Hello " + name + "!");

System.out.print("\nEnter your GPA: ");

//Notice you can take user input of different data types.

double GPA = scanner.nextDouble();
System.out.println("Your GPA is " + GPA + ".");

//Good practice to close the scanner.
scanner.close();
```

- Here is an example where we calculate the area of a rectangle:
```java
import java.util.Scanner;
  
public class userInput{

	public static void main(String[] args){
	
		//Create an object (scanner) of the Scanner class
		
		Scanner scanner = new Scanner(System.in);
		
		double width = 0;
		double height = 0;
		double area = 0;
		
		System.out.print("Enter the width: ");
		width = scanner.nextDouble();
		
		System.out.print("Enter the height: ");
		height = scanner.nextDouble();
		
		area = width * height;
		
		System.out.println("The area is: " + area + ".");
		
		//Good practice to close the scanner.
		scanner.close();
		
	}
}
```