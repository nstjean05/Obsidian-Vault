#### Type Compatibility Strategies
1. **By Name** (explicit)
	- Two items must be formally declared of the same type to be compatible.
2. **By Structure** (implicit)
	- Two items are compatible if they have the same structure.
```
type
	Array1 = array[0..5] of float
	Array2 = array[0..5] of float
	Array3 = Array2
var
	a1:Array1
	a2:Array2
	a3:Array3
	...
	a2 = a1;
	a3 = a2
```
- Note: Most languages have a mix of the two except that...
	- Literate languages lean toward the first
	- C-like languages lean toward the second
3. **Sub-Types**
	- A subtype is compatible with its parent type.
	- e.g. In ISO