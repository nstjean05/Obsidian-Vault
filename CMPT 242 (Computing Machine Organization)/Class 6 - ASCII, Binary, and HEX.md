6.  _ASCII, Binary, Hexadecimal representation, widening the representation, IEEE floating point 3.8, 3.9, 3.17-3.20_

a. Look up EBCDIC character coding and give an explanation of how it worked and compared to ASCII.
- This was created by IBM in the 1960s as one of the first-ever standardized character sets. It used 8-bit encoding to reserve a 256 English characters/symbols, which an IBM mainframe could then use to understand text. ASCII was developed around the same time (IBM helped to develop it), and was a standardized across manufacturers. It used a 7-bit system to reserve 128 characters, which left 127 extra values for programmers to use as they like.

b. Design and hand in a circuit that would divide a clock signal by 10. You have only 8-bit counters.
- 

c. (lookup) Is an Intel chip big or little endian? (Later I may ask you to write a program demonstrating this, so be sure you understand the concept. Give me your reference too. )
- A big endian describes a computer which stores bytes of int values from the most to the least significant. Little endian stores from the other direction (Ch. 3.10). Intel processors have generally expected little-endian values, with some exceptions (such as the Intel 8051) depending on the variant/use of the value.

d. (bonus) Besides using multiple F.A. circuits (one per bit) find a way to build a multiple bit adder, design the circuit and print it out, then show by the truth table it is correct. You need only extend it to two bits. If that much works, you can obviously extend it further.

