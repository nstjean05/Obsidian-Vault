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
- Languages use letters *A - F* (representing 9 - 15) to the set of decimal digits.
![[Pasted image 20250916141942.png]]
- Here is an example of how a binary string corresponds to hex
![[Pasted image 20250916142128.png]]
## 3.7 - Notation For Hexadecimal And Binary Constants
- Since a number can have ambiguous value when using different bases, mathematicians use subscripts to denote when a value isn't base 10.
	- For example, 125$_1$$_6$ denotes hexadecimal.
	- 125$_1$$_6$ = (1 * 16$^2$ ) + (2* 16$^1$ ) + (5 * 16$^0$ ) = 293$_1$$_0$
	- 293$_1$$_0$ = $\frac{293}{16}$ = 18 remainder 5, digit 0.
			$\frac{18}{16}$ = 1 remainder 2, digit 2.
			$\frac{1}{16}$ = 0 remainder 1, digit 3.
		- 293$_1$$_0$ = 125$_1$$_6$
- Depending on the base, there may also be a prefix.
	- **Hex**: 0x
	- **Binary**: 0b
- So to specify the 32-bit value in section 3.6, we would write **0xDEC90949**
## 3.8 - Character Sets
- Although a string of bits have no inherent meaning, there are standardized meanings for things like characters.
	- 1960s, IBM created EBCDIC, one of the first standardized character sets.
	- 1963, ASCII became a standard used across manufacturers, created by ANSI.
		- 128 characters, and additional bytes for symbols (escape, del, etc.)
		- Only seven bits are needed to represent an ASCII character.
		- There could be a max of 255 values, but only 128 leaves room for unconventional customization by programmers.
		- Below are the 128 characters, with their ASCII counterpart.

| Hex | Char | Hex | Char | Hex | Char    | Hex | Char | Hex | Char |
| --- | ---- | --- | ---- | --- | ------- | --- | ---- | --- | ---- |
| 00  | NUL  | 01  | SOH  | 02  | STX     | 03  | ETX  | 04  | EOT  |
| 05  | ENQ  | 06  | ACK  | 07  | BEL     | 08  | BS   | 09  | TAB  |
| 0A  | LF   | 0B  | VT   | 0C  | FF      | 0D  | CR   | 0E  | SO   |
| 0F  | SI   | 10  | DLE  | 11  | DC1     | 12  | DC2  | 13  | DC3  |
| 14  | DC4  | 15  | NAK  | 16  | SYN     | 17  | ETB  | 18  | CAN  |
| 19  | EM   | 1A  | SUB  | 1B  | ESC     | 1C  | FS   | 1D  | GS   |
| 1E  | RS   | 1F  | US   | 20  | (space) | 21  | !    | 22  | "    |
| 23  | #    | 24  | $    | 25  | %       | 26  | &    | 27  | '    |
| 28  | (    | 29  | )    | 2A  | *       | 2B  | +    | 2C  | ,    |
| 2D  | -    | 2E  | .    | 2F  | /       | 30  | 0    | 31  | 1    |
| 32  | 2    | 33  | 3    | 34  | 4       | 35  | 5    | 36  | 6    |
| 37  | 7    | 38  | 8    | 39  | 9       | 3A  | :    | 3B  | ;    |
| 3C  | <    | 3D  | =    | 3E  | >       | 3F  | ?    | 40  | @    |
| 41  | A    | 42  | B    | 43  | C       | 44  | D    | 45  | E    |
| 46  | F    | 47  | G    | 48  | H       | 49  | I    | 4A  | J    |
| 4B  | K    | 4C  | L    | 4D  | M       | 4E  | N    | 4F  | O    |
| 50  | P    | 51  | Q    | 52  | R       | 53  | S    | 54  | T    |
| 55  | U    | 56  | V    | 57  | W       | 58  | X    | 59  | Y    |
| 5A  | Z    | 5B  | [    | 5C  | \       | 5D  | ]    | 5E  | ^    |
| 5F  | _    | 60  | `    | 61  | a       | 62  | b    | 63  | c    |
| 64  | d    | 65  | e    | 66  | f       | 67  | g    | 68  | h    |
| 69  | i    | 6A  | j    | 6B  | k       | 6C  | l    | 6D  | m    |
| 6E  | n    | 6F  | o    | 70  | p       | 71  | q    | 72  | r    |
| 73  | s    | 74  | t    | 75  | u       | 76  | v    | 77  | w    |
| 78  | x    | 79  | y    | 7A  | z       | 7B  | {    | 7C  | \|   |
| 7D  | }    | 7E  | ~    | 7F  | DEL     |     |      |     |      |
## 3.9 - Unicode
- Some languages have many more characters than most European languages.
	- To accommodate this, there are some extensions and alternate methods of representing characters.
- **Unicode** is a standard for extended character sets.
	- It extends ASCII, and is intended to make character sets possible for all languages.
	- The current unicode standard defines ~150,000 symbols, including emojis.
## 3.11 - Signed Binary Integers
- A signed number means that it is positive or negative.
- There are 3 representations for *signed integers*:
	- **Sign Magnitude**: For an int of *k* bits, the most significant bit is interpreted as the sign (1 if the number is negative, otherwise 0). The remaining *k - 1* bits are the unsigned integer that specifies the absolute value.
	- **One's Complement**: A positive integer uses the same positional representation as an unsigned integer, making the maximum value of a k-bit integer (2$^k$$^-$$^1$ - 1), since the most significant digit is 0. To form the negative:
		- Flip each bit of the positive number.
	- **Two's Complement**: A k-bit two's complement integer uses the same positional representation as an unsigned int, with exception that the most significant bit has the value -2$^k$. To form the negative:
		- Take the positive binary value.
		- Flip each bit.
		- Add 1.
		- For example, take 010101.
		- Since the high-order bit = 0, the two's complement value is 21, the same as the unsigned value.
		- 010101 = (0 * -2$^5$) + (1 * 2$^4$) + (0 * 2$^3$) + (1 * 2$^2$) + (0 * 2$^1$) + (1 * 2$^0$) = 21
		- Another example, take 111100.
		- 111100 = (1 * -2$^5$) + (1 * 2$^4$) + (1 * 2$^3$) + (1 * 2$^2$) + (0 * 2$^1$) + (0 * 2$^0$) = -4
## 3.12 - Quirks of Signed Representations
- There are many oddities that result from signs.
	- Sign-Magnitude makes it possible to create the value of -0.
	- One's complement allows for two inverted values of zero (0000, 1111)
	- Two's complement includes one more negative value that positive.
## 3.13 - Example Of Two's Complement Numbers
- Below is a chart of nibbles and their various signed interpretations.
- Two's complement is the only one that doesn't have two zeroes.
![[Pasted image 20250916155525.png]]
- Unsigned and two's complement can use the same hardware operations for either representation.
## 3.14 - Sign Extension
- Computers support integers of various sizes (8, 16, 32, 64-bit, etc.)
- Occasionally a smaller value must be reassigned to a bigger one.
	- Ex. an *int* to a *long*
- In this case, the hardware must make the number 'longer' to fill the extra space.
- **Sign Extension** allows us to promote from *k-bits* to a larger size in 2's complement.
- Two examples:
	- **4-bit:** 1010      **8-bit:** 11111010
	- **16-bit:** 0000 0000 0000 0001      **32-bit**:0000 0000 0000 0000 0000 0000 0000 0001
- Determine if the first digit is 1 or 0 (negative or positive), and then paste that number throughout the high-order bits.
- A computer can use a single hardware circuit to perform both unsigned and two’s complement integer arithmetic; software running on the computer can choose an interpretation for the resulting bit strings.
## 3.17 - Range of IEEE Floating Point Values













## 3.18 - Biased Exponent Values













## 3.19 - An Example Floating Point Number













## 3.20 - Special Values And NaN

