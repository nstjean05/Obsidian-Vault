## Tree Data Structures
- Trees are non-linear structures wherein elements are organized into a hierarchy.
- A ***Search Tree*** is one whose elements are organized in such a way to make finding a specific one easier.
- A ***Binary Search Tree*** (BST) is a type of binary tree that for each node **n**:
	- the left subtree of **n** contains elements less than those stored in **n**.
	- the right subtree of **n** contains elements greater than those stored in **n**.
- To determine if a particular value exists within a BST:
	1. Start at the root.
	2. Compare target element at current node.
	3. Move left if target < node, move right if target > node.
	4. Concludes when the target == node.
## Why BSTs?
- They provide good logarithmic time performance in both the best and average cases.
- The below complexities were found while using a binary search algorithm:
![[Pasted image 20241031154007.png]]

## Adding a Node to a BST
- Adding is similar to finding elements (Start at root, follow path.)
- Adds as a leaf node.
- Below adds 77, 24, 58, 82, 17, 40, and 97 to a BST:
![[Pasted image 20241031154300.png]]

## Removing a Node from a BST
- There are three possible situations when removing a node:
	1. Node is a leaf.
		- Can simply be removed.
	2. Node has 1 child.
		- The deleted node is replaced by the child.
	3. Node has 2 children.
		- A replacement node is chosen to be the new parent.
		- Two ways of choosing:
			- Inorder Successor - the node containing the next highest value.
			- Inorder Predecessor - predecessor of p is the node q which comes just before p in the binary tree's inorder traversal.
- The link between peace, happiness, and the good life is... 
  Answer with one sentence, dont use the word "and"


Hey there!
