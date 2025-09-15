## 3.1 - Introduction
- Examination of binary representations used by computers for data.
	- Integer
	- Characters
	- Floating Point
- Show the consequences of representing data in binary.
## 3.2 - Definitions Of Bit And Byte
- **Bit** - Short for *Binary Digit*
	- Can Have two possible values.
	- Often represented in hardware as two voltage levels.
		- High/low or true/false
	- Software engineers generally use 0/1
- **Byte** - String of eight bits
	- This is needed as bits are too small in most applications
	- A byte contains eight hardware units, each holding a bit
	- These units work in parallel, delivering all eight bytes at the same time, giving the appearance of a single piece of hardware.
## 3.3 - Possible Values In A Byte
- A decimal number with *k* digits can represent a range of 10$^k$ digits.
	- Each bit can represent 2 possible values.
	- A byte generally has 8 bits.
	- A byte can represent 2$^8$ = 256 values.
		- Range 0 to 255
- In general, a data item occupying *k* bits can represent 2$^k$ possible values.
- For example, with 3 bits, 2$^3$ = 8 possible combinations.
	- 000, 001, 010, 011, 100, 101, 110, 111
- A bit has no intrinsic meaning, it only gains it by its interpretation.
## 3.4 - Binary Weighted Positional Representation
- Remember how to use base 10 - each position represents a power of 10.
	- For example, 123 = (1 * 10$^2$) + (2 * 10$^1)$ + (3 * 10$^0$)
- In the binary system, each position represents a power of two.
	- 









## 3.5 - Bit Ordering










## 3.6 Hexadecimal Notation Used By Humans










## 3.7 - Notation For Hexadecimal And Binary Constants










## 3.8 - Character Sets










## 3.11 - Signed Binary Integers

## 3.12 - Quirks of Signed Representations

## 3.13 - Example Of Two's Complement Numbers

## 3.14 - Sign Extension