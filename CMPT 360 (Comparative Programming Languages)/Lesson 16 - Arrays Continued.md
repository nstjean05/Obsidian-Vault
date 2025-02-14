#### Implementation of Arrays
- The compiler generates a descriptor:
	- Name
	- Element Type
	- Number of Dimensions
	- Index Type           (Repeat for each dimension)
	- Lowest Index       (Repeat for each dimension) (Omit of always 0)
	- Highest Index      (Repeat for each dimension)
	- Start Address      (Relative to end of code)
- All references to an array element require the compiler to compute an offset from the starting address to the item.
	- e.g. `A[rowCount, colCount]` or `Str[n]`
- This can become complicated, especially in a multi-dimensional array.
- Some languages store arrays by rows in column order, other by columns in row order.
- Actual memory storage is just consecutive items in this order.
#### Associative Arrays (Hash)
- These consist of a number of data items indexed by the same number of keys (not necessarily from a consecutive range)
	- e.g.            Key           Data
	           1033         Sutcliffe
	           1035         Smith
	           1029         Shantz
	           1061         Gibbons
	           1063         Perry