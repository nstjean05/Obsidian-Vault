#incomplete
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
###### 1: Whole Number Types
**Cardinal Numbers**
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
**Integer Types**
- In the range MIN(INTEGER)...MAX(INTEGER)
- These are stored in the same way in words of the same size as for Cardinal *but*:
	- The first bit in the sign 0 = positive and 1 = negative.
	- The digits are in 2s complement form.
		- Method:
			- Drop the sign
			- Represent the digits as cardinal
			- complement the digits, then add 1
	- e.g. Represent 12 in 8-bit 2s complement:
		12 = 0000 1100
		    1111   0011
					1    
		  = 1111 0100 = 12
	- Note that 1111 0100 as a cardinal is 244, which is 256-12 (2$^8$ - 12)
	- In 16 bits we would get 1111 1111 1111 0100 or 65524 as a cardinal:
		- 65536 - 12 or (2$^1$$^6$ - 12)
- There may be several whole types:
	- **cardinal**: OCTET, SHORTHAND, CARDINAL, LONGCARD etc.
	- **integer**: byte, short, int, long, etc.
###### Floating Point Types
- Model real numbers
- Are limited in both size & precision by storage size

**14.**  **_Basic_ _Data Types_**

**[3]** a. Assuming that integer types are stored in 16-bit format, show how the decimal numerals 427 and -501 are stored. Assume the most significant byte is first.
- To convert from decimal to hexadecimal (while retaining signs), we can use the 2s complement method. In this method, after conversion to base 16, the magnitude of the number is inverted, and one added to the total. The first bit of the value is known as the *sign bit*, which records the magnitude. 427 and -501 in 2's complement hexadecimal are 01AB and FE0B, respectively.
https://medium.com/@luischaparroc/integer-numbers-storage-in-computer-memory-47af4b59009

**[5]** b. Provide additional details about the IEEE 32-bit floating point format than were given in the class notes. Give the details of the IEEE 64-bit floating point format.
- IEEE outlines two fundamental formats for floating points -- single (32-bit) and double (64-bit) point precision. This format has three sections. (1) The Sign of Mantissa, which states that 0 indicated a positive number, and 1 a negative. (2) Rule of the Biased exponent, which states that the exponent field must represent *both* positive and negative exponents. (3) The Normalized Mantissa, meaning there cannot be more than a single 1 to the left of the decimal. A single-precision format has a precision of 24 bits (occupying 32 bits total), and double-precision formatting extends that to 53-bit precision  (occupying 64 bits in total). The double precision format is used for calculations which require a greater degree of accuracy, as it can store significantly more data.
https://docs.oracle.com/cd/E19957-01/806-3568/ncg_math.html
https://www.geeksforgeeks.org/ieee-standard-754-floating-point-numbers/

**[2]** c. What are the arguments for and against representing Boolean entities in a single memory bit?
- Boolean entities can be stored in a single bit of memory, as they hold a binary value. It can be useful to store it this way, as it takes up a very small amount of storage. However, storing boolean entities in a byte allows it to have a unique address. This advantage is significant, and as the amount of storage available is generally so large relative to the difference between a bit and a byte, picking the more versatile option is usually chosen. In some scenarios, where storage is highly limited, or boolean values are being stored in massive quantities such that the missing space is significant, storing in a single bit may be advantageous.
https://james-william-fletcher.medium.com/8-bools-in-1-byte-the-1-bit-boolean-cf6754b93230

**[2]** d. How does BCD waste memory?
- Binary Coded Decimal (BCD) is a method of recording decimals using 4 binary digits. This allows very precise values to be stored, although each value is capped at 9. However, as BCD values grow larger, the waste in storage grows similarly large. 
https://www.realdigital.org/doc/2c2b7d3170b8ae3af20b528e39942b98

**[3]** e. How does allowing coercion type transfer in a language weaken strong typing?
- 

**[3]** f. Compare the facilities for string manipulation found in the libraries of C++, ISO Modula-2, and Java.