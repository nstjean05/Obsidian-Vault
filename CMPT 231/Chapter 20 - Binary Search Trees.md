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
	5. 