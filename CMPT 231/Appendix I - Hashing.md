## What is hashing?
- A technique for sorting elements, potentially more efficiently than BSTs.
- Prior collections determined their elements order by...
	- ...recording the order in which elements were added.
	- ...comparing some key related to the element.
- Hashing determines location by some function of the value of the element.
	- Elements are stored in a *hash table*, with their location determined by a *hashing function*.
#### Hashing Structure
- Each location in a hash table is referred to as a cell or bucket.
	- Ex. We create an array that will hold 26 elements.
		- To store names, we create a simple hashing function that associates the first letter of each name to a separate cell.
			- First letter of the string determines the cell.
		- Access time to any single element is independent of the number of elements stored.
			- All operations are O(1)
		- However, it requires each element mapping to a unique position (called a perfect hashing function).
![[Pasted image 20241119152131.png]]

#### Collisions
- A *collision* occurs when 2 or more elements are mapped to the same location.
	- For example, two people whose names begin with the same letter.
- Even an imperfect hashing function (if it is still good) can result in O(1) operations.
###### Hash Table Size
- Now we must determine how large to make a table, to get as close as possible to the same size as our dataset.
	- Since a perfect hashing function would have a table of 100%, a good guideline for table size is to make is 150% of the dataset's size.
	- If the size of the dataset is unknown, we can use *dynamic resizing**














