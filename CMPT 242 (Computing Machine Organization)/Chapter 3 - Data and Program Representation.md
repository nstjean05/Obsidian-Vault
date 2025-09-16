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
	- Take the value *010101* or *111100*
	- 010101 = (0 * 2$^5$) + (1 * 2$^4$) + (0 * 2$^3$) + (1 * 2$^2$) + (0 * 2$^1$) + (1 * 2$^0$) = 21
	- 010101 = (1 * 2$^5$) + (1 * 2$^4$) + (1 * 2$^3$) + (1 * 2$^2$) + (0 * 2$^1$) + (0 * 2$^0$) = 60
- The binary numbers that can be represented with eight bits range 0 to 255.
- Modern hardware usually supports 32- and 64-bits (4 and 8 bytes respectively).
- Below shows the common powers of two in decimal values.
![[Pasted image 20250916140449.png]]
## 3.5 - Bit Ordering
- In **decimal**, the least significant digit is on the right, with the most on the left.
- In **binary**, the *Least Significant Bit* (LSB) is on the right, and the *Most Significant Bit* (MSB) is on the left..
- This system of left and right doesn't make as much sense in relation to physical hardware.
- **Bit ordering** becomes especially important when bits locations are transferred, as the same order must be preserved
## 3.6 - Hexadecimal Notation Used By Humans
- Numeric values can be written in decimal, but this does not specify the individual bit-values.
- For this, we can use base-16, a.k.a. hexadecimal.
- **Hexadecimal** encodes each group of four bits (a *nibble*) into a single **hex** digit.
- To express each hex digit as a single character, programming languages 








## 3.7 - Notation For Hexadecimal And Binary Constants










## 3.8 - Character Sets










## 3.11 - Signed Binary Integers

## 3.12 - Quirks of Signed Representations

## 3.13 - Example Of Two's Complement Numbers

## 3.14 - Sign Extension