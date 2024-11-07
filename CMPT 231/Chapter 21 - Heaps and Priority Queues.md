## What is a Heap?
- A complete binary tree where...
	- Min-heap -> each element is ≤ both of its children
	- Max-heap -> each element is ≥ both of its children
#### Adding a New Element
1. Add the element as a leaf, so that the tree remains balanced.
2. Exchange the element node-by-node upwards until its relationship amongst the elements linking it is appropriate
![[Pasted image 20241107142333.png]]
#### Removing the Min Element
1. Remove the root (min) and reconstruct the heap.
2. First, move the last lead of the tree to be the new root of the tree.
3. Then, move it down the tree until the relationships among the elements are appropriate.
	1. Specifically, compare the element to the smaller of its children and swap them if the child is smaller.
![[Pasted image 20241107142416.png]]






