2. **F  22.3-22.4 Basic circuits and transistors**

a. What is the difference between a pnp and an npn transistor?
- An NPN transistor effectively amplifies a positive signal applied to its base, whereas a PNP transistor allows current to flow if a negative voltage is applied to it. Often NPN transistors are used in electronics as they transfer energy very quickly, and are slightly cheaper to manufacture. PNP transistors can be useful in many scenarios as well. One such case is when working with oscillating signals, it can be beneficial to use a PNP and an NPN transistor in tandem to more efficiently amplify the signals.

b. What are the input and output value ranges for (i) 3V logic (ii) 5V logic?
	i) 3V Logic
		- The highest output the chip will produce is 2.4V, and the lowest is 0.4V.
		- The range of reliable inputs is from 0.8V to 2V.
	ii) Using 5V logic,
		- The highest output the chip will produce is 2.7V, and the lowest is 5V.
		- The range of reliable inputs is from 2V to 5V.

Textbook Questions:
**22.3** Design a circuit that uses _nand_, _nor_ and _inverter_ gates to provide the _exclusive or_ function.
* Completed in Class 1.

**22.4** Write a truth table for the full adder circuit in Figure 22.12.

|bit1|bit2|carry in|sum|carry out|
|---|---|---|---|---|
|0|0|0|0|0|
|0|0|1|1|0|
|0|1|0|1|0|
|0|1|1|0|1|
|1|0|0|1|0|
|1|0|1|0|1|
|1|1|0|0|1|
|1|1|1|1|1|
Arrow Electronics. (2025, January 15). _NPN vs. PNP in circuit design and industrial controls_. Retrieved October 26, 2023, from [https://www.arrow.com/en/research-and-events/articles/npn-vs-pnp-in-circuit-design-and-industrial-controls](https://www.arrow.com/en/research-and-events/articles/npn-vs-pnp-in-circuit-design-and-industrial-controls)
Tocci, R. J., Widmer, N. S., & Moss, G. L. (2001). _Digital systems: Principles and applications_ (8th ed.). Prentice Hall. [https://www.microchip.com/content/dam/mchp/documents/OTH/ProductDocuments/SupportingCollateral/chapter8.pdf](https://www.microchip.com/content/dam/mchp/documents/OTH/ProductDocuments/SupportingCollateral/chapter8.pdf)
All About Circuits. (n.d.). _Logic signal voltage levels_. Retrieved October 26, 2023, from [https://www.allaboutcircuits.com/textbook/digital/chpt-3/logic-signal-voltage-levels/](https://www.allaboutcircuits.com/textbook/digital/chpt-3/logic-signal-voltage-levels/)