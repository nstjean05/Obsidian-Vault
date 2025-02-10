#### Data Type Definition
- A **Data Type** is a specification for a category of data containers that includes:
	- What values an instance of the type can take on.
	- What operations may be performed on those instances.
- Data types may be:
	1. Simple (atomic, primitive, built-in)
		- That is, not defined in terms of simple types.
		- Usually mirror logically types available in hardware.
	2. Structured (array, record, (set))
		- Has parts that are simple types
	3. Abstract (ADT)
		- Their structure, internal representation, or parts is hidden.
		- They are **transparent**.
			- The structure, parts, and possibly aspects of their representation is visible and can be manipulated by the programmer.
- Variables of a data type may be thought of in terms of their attribute descriptors.
#### Typical Built-In Data Types
- These are generally abstract, with their parts (if any) and underlying representation invisible. This is done to:
	1. Protect these entities from undisciplined manipulation.
	2. Allow various implementations so software can be portable.
- Proper usage of this type is checked at compile time.
- Their operations are specified, but the range of legal values may depend on implementation restrictions in the OS and hardware.
##### Numeric Types (and compatible ones)
- Often have ambiguous operators (+ - * / modulus) where meaning must be disambiguated either by:
	1. Overloading via a library facility
	2. The language definition
- And this is done either at:
	1. Compile time.
	2. Interpretation (run) time - hard work for interpretation
- If scalar (comparable) types generally allow <, <=, >, >=, =, # comparisons and may have:
	- MAX/MIN     INC/DEC (if ordinal)
	- Accuracy control e.g. int, shortint, longint, float, long, double, etc. which are subranges of a parent type.
##### The Usual Suspects
- There are a few common places to look, should something go wrong.
1. **Whole Number Types**
	- Cardinals, in the range 0... max(cardinal)
	- Sometimes misleadingly called POSITIVe, but non-negative whole number is better.
	- These are stored in binary form in words Ia minimum data store - typically 2$^n$ 8-bit bytes.
		- e.g. in 8-bits 100$_1$$_0$ = 0110 0100 (base 2)
	- So if a word is:
		- 8 bits the range is 0..255
		- 16 bits...                 0..65535
		- 32 bits...                 0..2147483647
		- 64 bits...                 0..18446744073709551615 20 digits
	- The maximum for n bits is 2$^n$ -1
	- 