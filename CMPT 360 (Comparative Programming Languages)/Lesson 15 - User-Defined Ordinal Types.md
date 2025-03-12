#incomplete
#### Enumerations
- e.g. mon, tue, wed, thu, fri
- Are names values with an implicit ordering.
- In Pascal, C++, the names must be unique per program.
- In C the names are really int, in C++ they can be "cast" to int.
	- Generally "casting" is assigning a type to a variable which is not.
	- e.g. casting an int type as a float.
	- In the case of C++, "cast" is often colloquially defined as changing a variable's type.
- Typically in most languages the default underlying values or value to which they convert are 0... n
- In Modula-2, Ada, C#, and others the correspondence with numbers requires an explicit conversion.
```
		TYPE
			DayName = (sun, mon, tue, wed, thu, fri, sat)
		VAR
			day:DayName;
			...
			day := mon;
			card := ORD(day);                  (Card holds 1)
			INC(day, 2);                       (Day holds wed)
			day := MAX(DayName);               (Day holds sat)
			day := VAL(DayName, 3);            (Day holds wed)
			BUT day := day + 1                 (Error)
```
- In ISO Modula-2 and Ada BOOLEAN and CHAR(ACTER) are built-in enumeration types.
- Per *t* a language may restrict arithmetic correctly.
#### Subranges
- Are subtypes of consecutive values of an ordinal type.
- e.g$_1$. TYPE WeekdayName = (mon..fri)
- e.g$_2$. type DAYNAME is (sun, mon, tue, wed, thu, fri, sat)
	  subtype WEEKDAYS is Days range mon..fri
	  subtype DIGIT is INTEGER range 0..9
- The usual rules:
	- Subranges and other subtypes are compatible with the parent type.
	- But derived types are not (they are treated as brand new types)
	- (Ada) Type derived type is a new DAYS range mon..fri
- In Modula-2 subranges of enumeration types inherit the numbering from the parent type so that in WeekdayName (above) the numbering is 1..6 not 0..5
	- This may or may not be the rule in other languages.
- Here are some potentially useful examples from literate languages:
```
TYPE
	UpperCase = "A".."Z"; //Works because char is an enumeration
	LowerCase = "a".."z"; //...
	
	MonthNum = 1..31;
	WeekNum = 1..53;
	DayNum = 1..7;

	ArrayIndex = 0..maxIndex; //Previously defined
```
#### Finite Mappings
- These are mappings from an ordinal range to a set of values.
- We think of them as indexed collections under one identifier
	- A.K.A arrays
- In Math a$_1$ a$_2$ a$_3$ a$_4$ ... a$_n$ translate to early notations a(1) a(2) a(3)... a(n)
	- **Problem**: Ambiguous to function calls (Non-orthogonal parenthesis)
	- **Why?** Brackets [ ] weren't on keyboards
	- Modern (usually) a[0], a[1], a[2],... a[n-1]
- Many languages require indexing to start at 0
	- Java, C, C++, Modula-2 R10
- Others fix the start index at 1 (Fortran)
- Others allow any ordinal range of indices
	- Modula-2, ISO, Ada
- However, array contents are always from the same type.
	- i.e. array[1] cannot be type *float* while array[2] is *int*
- **Issue**: Does the language require the compiler to check index values?
- **Solution**: Put in your own index checks before using an index.
#### Classification of Array Attributes According to Binding Time
1. The index type and contents type - usually static
2. Other attributes (index subscript values, storage, overall size)
	1. Static (very efficient)
	2. Fixed stack-dynamic (indices static, storage dynamic)


**15.  _Data Aggregates - arrays_**

**[3]** a. What are the differences between subtypes and derived types in Ada?
- The primary difference between a subtype and its derived type is that subtypes, of the same given type, will be compatible with one another and their base type. Derived types, on the other hand, are distinct from one another their base type. In other words, a derived type is a completely new type, while subtypes can still be compared to their base.
https://stackoverflow.com/questions/2677752/derived-types-and-sub-types-in-ada

**[3]** b. What justification is there for the -> operator in C and C++?
- As the textbook notes, the *->* operator is used to refer to a field within a record. This is used in C(++) to assign a value at a specific address, while taking on that address's assigned type. Although this was possible using other methods (* and .), they were more roundabout. Later on, additional functionality made using the deference and dot operators do the same thing, leaving -> somewhat redundant.
https://stackoverflow.com/questions/13366083/why-does-the-arrow-operator-in-c-exist

**[3]** c. What are the differences between enumeration types in C++ and Java?
- Enumeration (enum) types are data types wherein its composite constants are given in its definition. There are many differences between these types in C++ and Java. For instance, in Java all enumeration types are subtypes of the greater (predefined) *Enum* class. C++, as one of the first two languages to utilize enumeration, has more open-ended, non-coercive application. Java has the advantage of being more reliable, as it gives errors for arithmetic operations and limits the values assigned to variables. C++ has less restrictions, only checking variable types (on assignment), and if they are in the enum's given range.