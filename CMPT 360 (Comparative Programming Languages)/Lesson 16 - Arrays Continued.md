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
	- e.g.            *Key*           *Data*
	           1033         Sutcliffe
	           1035         Smith
	           1029         Shantz
	           1061         Gibbons
	           1063         Perry
		- A portion of an array called *18th Ave*
- The index keys have to be stored as well as the data because they are not in a consecutive range of ordinals.
- Some associative array arrangements allow the index to be any type, including, say, a string.
- In Perl such AA's have names beginning with %.
- In most environments AA's would be implemented in a library, not in the language per se.
- A more complex hash might have several items with the same index - each hash is a category.
#### Cartesian Products
- Also known as cross products.
	- In computing science, we can use different data types as (x,y,z...) in a coordinate and call them a *record*.
	- Each component of the record (x,y,z) is called a field.
- Here, each entity of a type that defines ordered tuples with each coordinate from a different base type.
	- e.g. `(15, "Ted", "Aug12 1986", 2.56, -3)`
			int.   str.               str.                float.    int.
- These are c