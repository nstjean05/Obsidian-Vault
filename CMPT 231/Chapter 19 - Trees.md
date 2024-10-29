#computer-science
## What is a Tree?
- A tree is a non-linear structure in which elements are organized hierarchically.
- Each element is stored in a node, and connected by edges.
	- Connecting to a node will change the level that node is on.
	- There can only be one *root* node on a tree.
	- Lower-level nodes are called children (of the previous level).
- Each node only has one parent, but each parent may have many children.
	- Only the root node has no parent.
	- A node with no parent is called a *leaf* node.
	- If one node is far above another on the tree, it is an *ancestor*.
- The *height* of a tree is the ∆ in levels between root and the farthest leaf.

![[Pasted image 20241017151737.png]]

#### Tree Classifications
###### Order of the Tree
- Maximum number of children a node is allowed to have.
###### General Trees
- No limit to the number of children a node may have.
###### n-ary Tree
- A tree that limits each node to no more than ***n*** children.
###### Binary Trees
- Nodes may have at most two children.
###### Balanced Trees
- All leaves of a tree are within one level of one another.
###### Full Tree
- An n-ary tree is *full* if both:
	- All leaves are at the same height;
	- Every non-leaf node has *exactly* n children.
###### Complete Tree
- A Tree is complete if:
	- It is full, or full to the next-to-last level.
	- Nodes have either n or zero children.

###### Example
- Each of the trees (a, b, c) are ***complete*** - they are full to at least the second-last level, and all nodes either have n or zero children.
- Only tree **c** is ***full***, as is is the only one where all leaves are of the same height.

![[Pasted image 20241017153841.png]]

## Implementing Trees

##### Linked Structures
- This is the most obvious choice for implementing trees.

##### Array-Based
- Although these are a less obvious implementation, they are still sometimes useful.
- They may be used if the tree is full or complete.
- Below are two strategies.
###### Computed Child Links
- For any element stored in position n:
	- The element's left child is stored in array position (2n+1)
	- The element's right child is stored in array position (2*(N+1))
- If the tree is not near complete, then is approach is a massive waste of array space.

![[Pasted image 20241017155511.png]]
###### Computed Child Links
- Each element of the array is stored in an object, which stores a reference to the tree element and the array index of each child.
- Array positions are allocated on a first-come, first-serve basis.
## Tree Traversals

**Pre-Order**
- Visit the root, then traverse subtrees L to R.

**In-Order**
- Traverse the left subtree, root, then right subtree.

**Post-Order**
- Traverse subtrees from L --> R, then visit the root.

**Level-Order**
- Visit each node, at each level, top to bottom, left to right.

![[Pasted image 20241029151339.png]]

## Binary Tree ADT
- ADT = Abstract Data Type (or Class)
###### Operation - Description
	getRoot            - Returns a reference to the root of the binary tree.
	isEmpty.           - Determines if the tree is empty.
	size               - Returns the number of elements in the tree.
	contains           - Determines whether a specified target is in the tree.
	find               - Returns a reference to the specified target if it's found.
	toString           - Returns a string representation of the tree.
	iteratorInOrder    - Returns an iterator for an inorder traversal of the tree.
	interatorPreOrder  - ... preorder traversal ...
	interatorPostOrder - ... postorder ...
	iteratorLevelOrder - ... levelorder ...
## Expression Trees
- A tree that shows that relationship between operators and operands of an expression.
- Evaluated from the bottom-up.
- The following example uses a 