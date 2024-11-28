- A multi-way search tree combines the concepts of:
	- General trees, with multiple children per node.
	- BSTs, with relationships among elements but only 2 trees per node.
	- In multi-way search trees, each node may have more than 2 children, with a specific relationship between the elements.
## 2-3 Tree Basics
- In a 2-3 tree, each node has 2 or 3 children.
- **2-Node**
	- Contains one element
	- Can have 2 or no children.
	- Left tree contains elements less than the node, and right subtree contains those greater.
- **3-Node**
	- Contains two elements.
	- Can have 3 or no children.
	- If the node has no children, there may be either one or two values held in that node.
	- If the node has children, the left one is less than it, the right one is greater than it, and the one in the middle is has the value:
		- Left ≤ Middle ≤ Right.
- *Underflow* is when we must rotate the tree or reduce its height to maintain the 2-3 properties.
## Inserting Elements into 2-3 Trees
- The tree is searched to find the proper leaf, where the new element is inserted.
	- If there is one element in leaf then the new element will be inserted beside it.
	- If there are two elements in the leaf, then the new element will be inserted according to its size, with the elements ordered smallest to largest, left to right.
	- Whichever the middle element ends up as, will go to its parent node.
	- This process continues until there is only 2 elements in a node.
![[Pasted image 20241128150228.png]]