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
			:
		day := mon;
		card := ORD(day);                        (Card holds 1)
		INC(day, 2);                                   (Day holds wed)
		day := MAX(DayName);               (Day holds sat)
		day := VAL(DayName, 3);            (Day holds wed)
		BUT day := day + 1                       (error)
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
- In Modula-2 subranges of enumeration types inherit 