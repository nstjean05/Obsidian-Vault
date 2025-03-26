#incomplete 
### Object Oriented Basics
- Procedural languages are activity-centric.
	- The programmer passes information about an entity to a procedure and it takes action and/or computes results.
	- `PROCEDURE Area (len, wid:REAL):REAL;`
```
TYPE
	Rectangle = 
		RECORD
			length, width : REAL
			area, perimeter L REAL;
		END;
rect.area = Area(leangth, width)

```
- The object oriented style is *data-centric* or (better) *entity-centric*
- Object entities do not depend on procedures/functions declared elsewhere.
	- Rather, they own and control not only their own data but also the means to manipulate it.
	- Ex. The attributes length and width, as well as the methods (message carrier) 