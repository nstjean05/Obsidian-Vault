#### Enumerations
- e.g. mon, tue, wed, thu, fri
- Are names values with an implicit ordering.
- In Pascal, C++, the names must be unique per program.
- In C the names are really int, in C++ they can be "cast" to int.
	- Generally "casting"
- Typically in most languages the default underlying values or value to which they convert are 0... n
- In Modula-2, Ada, C#, and others the correspondence with numbers requires an explicit conversion.
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
- In ISO Modula-2 and Ada BOOLEAN and CHAR(ACTER) are built-in enumeration types.
- 