#computer-science
### Method 1: Selection Sort
###### Steps:
1. Scan from left to right, determine the smallest element.
2. Swap the smallest element into the first position (P1).
3. Scan from left to right (starting at P2), determine the smallest element.
4. Swap the smallest element into P2.
5. Continue this until each element is in order.
###### Run-Time Complexity:
O(n^2) - Horrible Efficiency.
###### Animated Example:
![https://upload.wikimedia.org/wikipedia/commons/6/6d/Selsort_de_0.gif](https://upload.wikimedia.org/wikipedia/commons/6/6d/Selsort_de_0.gif)
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
![https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif](https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif)
###### Code Example:
```java
public static <T extends Comparable<T>>
void insertionSort(T[] data)
{
	for (int index = 1; index < data.length; index++)
	{
		T key = data[index];
		int position = index;
		// shift larger values to the right
		while (position > 0 && data[position-1].compareTo(key) > 0)
		{
			data[position] = data[position-1];
			position--;
		}
		data[position] = key;
	}
}
```
### Method 3: Bubble Sort
###### Steps:
1. Compare the Element 1 (E1) and E2. If the one on the right is greater than the left, swap their positions.
2. Compare E2 and E3. Swap if necessary.
3. Compare E3 and E4. Swap if necessary.
4. Continue until all elements are sorted.
###### Run-Time Complexity:
O(n) - Excellent/Good/Fair/Bad/Horrible
###### Animated Example:
https://upload.wikimedia.org/wikipedia/commons/c/c8/Bubble-sort-example-300px.gif
###### Code Example:
```java
public static <T extends Comparable<T>>
void bubbleSort(T[] data)
{
	int position, scan;
	T temp;
	for (position = data.length - 1; position >= 0; position--)
	{
		for (scan = 0; scan <= position - 1; scan++)
		{
			if (data[scan].compareTo(data[scan+1]) > 0)
			swap(data, scan, scan + 1);
		}
	}
}
```

### Method 4: Quick Sort
1. Consider any one element. Pick the elements on far left and right, and then sort the three into order. Now place them back in their position based on order.
###### Animated Example:
https://commons.wikimedia.org/wiki/File:Quicksort-example.gif
###### Code Example:
```java
public static <T extends Comparable<T>>
void quickSort(T[] data)
{
	quickSort(data, 0, data.length - 1);
}

/**
* Recursively sorts a range of objects in the specified array using the
* quick sort algorithm.
*
* @param data the array to be sorted
* @param min the minimum index in the range to be sorted
* @param max the maximum index in the range to be sorted
*/
private static <T extends Comparable<T>>
void quickSort(T[] data, int min, int max)
{
	if (min < max) {
		// create partitions
		int indexofpartition = partition(data, min, max);
		// sort the left partition (lower values)
		quickSort(data, min, indexofpartition - 1);
		// sort the right partition (higher values)
		quickSort(data, indexofpartition + 1, max);
	}
}


/**
* Used by the quick sort algorithm to find the partition.
*
* @param data the array to be sorted
* @param min the minimum index in the range to be sorted
* @param max the maximum index in the range to be sorted
*/
private static <T extends Comparable<T>>
int partition(T[] data, int min, int max)
{
	T partitionelement;
	int left, right;
	int middle = (min + max) / 2;
	// use the middle data value as the partition element
	partitionelement = data[middle];
	// move it out of the way for now
	swap(data, middle, min);
	left = min;
	right = max;
	while (left < right)
	{
		// search for an element that is > the partition element
		while (left < right && data[left].compareTo(partitionelement) <= 0)
			left++;
		// search for an element that is < the partition element
		while (data[right].compareTo(partitionelement) > 0)
			right--;
		// swap the elements
		if (left < right)
			swap(data, left, right);
	}
	// move the partition element into place
	swap(data, min, right);
	return right;
}
```

### Method X: YYY Sort
###### Steps:
1. 
###### Run-Time Complexity:
O(n) - Excellent/Good/Fair/Bad/Horrible
###### Animated Example:
https:Link
###### Code Example:

``` java
System.out.println("Hello World");
```


![[Pasted image 20241015153947.png]]

