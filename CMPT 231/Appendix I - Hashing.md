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
	- If the size of the dataset is unknown, we can use *dynamic resizing* to create a larger hash table and transfer the elements.
###### Dynamic Resizing
- When should you resize?
	a) When the table is full.
	- Although this is an option, the performance of a hash table degrades greatly as it nears its capacity.
	b) As it nears its load factor.
	- A percentage of table occupancy at which the table will be resized.
## Hashing Functions
- The goal of a hashing function is to:
	- Scramble the keys uniformly
	- Compute efficiently
	- Make each table position equally likely for each key.
- Example: Social Insurance Numbers
	- **Bad**: Sort by the first three digits (First digit identifies province of SIN registry)
	- **Better**: Sort by the last three digits
	- This example can be replicated in numerous contexts, such as:
		- Birthdays - birth date is better than birth year.
		- Phone numbers - final digits are better than the first digits.
###### Approaches to Hashing Functions
- Extraction
	- Part of an element's key value is used to compute the location.
- Division
	- Computing the location mathematically
	- Hashcode (key) = Math.abs(key) % p
		- For some positive integer p, the result will be in the range 0 to p-1
- Folding
	- The key is divided in two parts, which are combined (folded) together to create an index.
	- **Shift** and **Boundary** folding:
	1. Divide the key into two parts, where each part is the same length as the desired key.
		- **Shift Folding**: these parts are added to create the index.
		- **Boundary Folding**: Some parts are reversed before adding.
- Mid-Square
	- The key is multiplied by itself and then the extraction method is used (take digits from the middle).
- Radix Transformation
	- The key is transformed to another numeric base
	- Then use the division method, and divide the new key by the table size, using the remainder as the index (mod).
- Digit Analysis
	- Extract and then manipulate specific digits from the key.
		- Ex. Take out (in order) from the 3rd to 6th digits, and them transform them in some way.
- Length-Dependent
	- The key and its length are combined in some manner to form the index, or part of it.
###### Hashcode
- The *object* class defines a method called *hashcode* which returns a memory location of the object.
- Usually not useful, but makes sure that every object has a hashcode method.
- hashcode() returns a 32-bit int between -2147483648 and 2147483647.
	- Bugs: Don't use code%M or (Math.abs(code)%M) as the index for an array.
	- You may use ((code & 0x7fffffff) % M)) as the array index.
## Resolving Collisions
- With *M* bins, it is expected that two objects will enter the same bin after √π(M/2) entries.
- A collision is when two keys map to the same location in a hash table.
- There are two main ways to resolve collisions:
	- Separate Chaining
	- Open Addressing (linear probing, quadratic probing, double hashing)
###### Separate Chaining (Chaining with Links)
- Use an array of M < N linked lists.
	- Hash: map key to integer i between 0 and (M - 1)
	- Insert: it at the front of the chain if it isn't already there.
	- Search: only need to search in the chain.
- Load factor (lambda): is the ratio of (#Elements)/(Table Size)
	- In separate chaining, the load factor is the average number of elements in a bucket.
	- Not safe for (lambda) > 0.5
###### Open Addressing
- No chaining, as each key fits in the hash table.
- Probe Sequence:
	- h(k)
	- (h(k) + f(1)) mod HSize
	- (h(k) + f(2)) mod HSize
	- ...
- Lazy deletion is needed for this method.
	- Mark a location as deleted, if the 'deleted' key resides there
- **Linear probing** is the simplest approach to finding a new unused position
	- If a location is occupied, go to (p+1)%s, where p is position, % is mod, and s is size.
	- Primary issue with this method is the '*primary clustering*' of occupied cells.
- There are other approaches to open addressing as well.
	- **Quadratic Probing**: (p + i^2)%s
						- Not safe for (lambda) > 0.5
	- **Double Hashing**: Creates a second hash function with a different index pattern.
						- Safe for (lambda) < 1
## Deleting Elements
There are 5 cases for removing an element from a chained implementation.
 If the element is...
1. Uniquely mapped, simply remove it.
2. Stored in the table, but has an index into an overflow area.
	- Replace the element and the next index value in the table with the element and next index value of the array position pointed to by the element to be removed.
3. At the end of the list of elements.
	- Set its position to null
	- Set the next pointer of the previous element to null.
	- And add that position to the overflow.
4. In the middle of the list.
	- Set its position in overflow to null
	- Reset the pointer of the previous element to skip it.
5. If the element is not in the table, throw an exception.
##### Rehashing
- When the table gets too full, create a larger table (usually 2x the size) and hash all the items into the new table.
- When to rehash?
	- Half full (lambda = 0.5)
	- When an insertion fails.
	- Some other threshhold.
## Hashing Versus Balanced Trees
- Hashing:
	- Simpler to code.
	- No effective alt for unordered keys.
	- faster for simple keys (few operations).
	- Java has better system support.
	- Need to make sure that your function produces suitably random values.
- Balanced Trees:
	- Stronger performance guarantee.
	- Can support many more operations for ordered keys.
	- Easier to implement compareTo() correctly than equals() and hashcode()
- Java Includes Both:
	- Red-black trees w/ java.util.TreeMap or java.util.IdentityHashMap
	- Hashing: java.util.HashMap or java.util.IdentityHashMap










