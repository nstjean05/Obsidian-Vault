### What is a Tree?
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

