- Complete 7.1-7.3
## 7.1 - Introduction
- Discussion of the assembly languages used to specify instructions and operands.
## 7.2 - The Reason to Learn Assembly Language
- All programming used to mean writing in assembly, before higher level languages were written.
- It may be necessary to know assembly during debugging.
	- Compilers sometimes have flaws which generate the wrong assembly, and you need to know how to fix it.
## 7.3 - Characteristics of High-Level Languages
- There are many paradigms to contrast high level (C, Java, Python) and low level assembly languages.
- **One to Many | One to One**
	- Compiler translates one high-level statement into many low level statements.
- **Hardware Independence | Hardware Dependence**
	- You don't need to know the hardware details when writing at a high level.
	- Programmer can add two variables without knowing the assembler.
	- Assembly requires the exact instruction set to be known and specified for addition.
- **General Purpose | Special Purpose**
	- High-level language makes building arbitrary applications easy for the programmer.
	- It's hard to build an application in Assembly, but has the ability to create very special-purpose code.
- **Abstractions**
	- Abstractions are provided in high-level language for many functions, which make structuring a large program much easier.
	- There is very little abstraction in Assembly language.
