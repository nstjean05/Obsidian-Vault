### Method 1: Selection Sort
###### Steps:
1. Scan from left to right, determine the smallest element.
2. Swap the smallest element into the first position (P1).
3. Scan from left to right (starting at P2), determine the smallest element.
4. Swap the smallest element into P2.
5. Continue this until each element is in order.
###### Efficiency:
O(n^2)
###### Animated Example:
https://upload.wikimedia.org/wikipedia/commons/6/6d/Selsort_de_0.gif
###### Code Example:
```java
public static <T>
	boolean linearSearch(T[] data, int min, int max, T target)
	{
		int index = min;
		boolean found = false;
		while (!found && index <= max)
		{
		found = data[index].equals(target);
		index++;
	}
	return found;
}
```

### Method 2: Insertion Sort
###### Steps:
1. Consider the first element of the list to be a sorted sublist of length 1.
2. Consider a second item from the list, and check from left to right until it is between a smaller and larger number.
3. Continue until all elements are sorted.

###### Animated Example:
https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif

### Method 3: Bubble Sort
###### Steps:
1. Compare the Element 1 (E1) and E2. If the one on the right is greater than the left, swap their positions.
2. Compare E2 and E3. Swap if necessary.
3. Compare E3 and E4. Swap if necessary.
4. Continue until all elements are sorted.
###### Animated Example:
https://upload.wikimedia.org/wikipedia/commons/c/c8/Bubble-sort-example-300px.gif

### Method 4: Quick Sort
1. Consider any one element. Pick the elements on far left and right, and then sort the three into order. Now place them back in their position based on order.
###### Code Example:

``` java
System.out.println("Hello World");
```

#computer-science
