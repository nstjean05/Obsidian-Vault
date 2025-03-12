#incomplete
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
- These are called *records* or *structures* in Algol-like notations.
- References within the cross product are not by position number (1,2,3...) but by the *name* of the position (or *field*) as defined in the type definition. For instance, the one above could be:
```
TYPE
	PersonalRecord = 
		RECORD
			index : cardinal;
			firstName : Str;
			birthDate : Str;
			GPA : FLOAT;
			points : INTEGER;
		END;
	VAR
		P : PersonalRecord;
	...
		p.index := 20;
		p.GPA := 3.05;
```
#### Operations on Records
- ... Are limited to construction (assignment) and inspection (checking, using a field)
- COBOL allows assignment of corresponding fields from one record to another (ignoring others).
- The line `MOVECORRESPONDING RecordA TO RecordB` will copy *all* fields named the same from one to the other (assuming the fields are the same type for each name), even if RecordA and RecordB are different types and the fields are not in the same order.
- Oberon allows for records to be extended to allow for OO.
- Pascal and Classical/ISO Modula-2 have discriminated (variant) fields based on a tag field or discriminator.
- Modula-2 R10 has indeterminate record types.
- Several languages use record constructors, such as:
	- `birthDate := Date{Jul, 3, 1947}`
	- Some infer the type, don't need it explicit.
#### Record Attributes
- Are stored in a compile-time descriptor.
- As usual





**16.  _Data Aggregates - records, etc_**

(You need to know how to explain in your own words the difference between discriminated and undiscriminated unions.)


**[3]** a. What is the difference between structs in C++ and C#
- There are several differences between structures (structs) in these two languages. In C++, structs resemble classes, including features like polymorphism and inheritance. C#'s structs do not support either of those features, as they are value types.
https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/value-types

**[3]** b. How do Python's tuple types differ from records?
- In Python a record is a similar to a struct, utilizing named fields and are often used for recording/accessing data. Tuples, on the other hand, are fixed sets of values, generally used temporarily and at smaller scale.
https://stackoverflow.com/questions/4212265/tuples-vs-records

**[3]** c. What is a list type in LISP and Scheme? Give at least one example of how to use one.
- Lists (in LISP and Scheme) are rudimentary data structures, which can hold elements. They can store a variety of data types, and even a combination of multiple. For example you could declare a list function, and have multiple sub-functions which can check for a certain element in the list, how many elements are in the list, if the list is empty, and so on. This has a variety of applications from simple to-do lists to extensive business ledgers.

**[3]** d. In what way is static type checking better than dynamic type checking?
- The primary advantages of static type checking is that errors can be detected much faster, and that the code can run faster. Both of these are due to the way which compilers interact with code. Static type checking verifies types during compile-time, which means that the errors are caught earlier, and the code is able to run faster as there is less to check at runtime.