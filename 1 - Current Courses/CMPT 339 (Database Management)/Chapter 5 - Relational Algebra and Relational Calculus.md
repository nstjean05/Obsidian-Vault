## Homework 2
**Part 1**
a. $\Pi_{\text{equipNo, description, dailyRate}}(\sigma_{\text{category} = vision}(\text{Equipment}))$
b. $\Pi_{\text{firstName, lastName}}(\sigma_{(\text{year} \geq 3) \,\land\, (\text{program = Computing Science})}(\text{Student}))$
c. $\Pi_{\text{equipNo, description}}(\sigma_{\text{dailyRate} ≤ 18}(\text{Equipment}))$
d. $\Pi_{\text{studentNo, firstName, lastName, description}}\big((\text{Student} \bowtie \text{Loan}) \bowtie \text{Equipment}\big)$
e. $\Pi_{\text{equipNo, description, firstName, lastName}}\big(\text{Equipment} ⟕ ((\text{Loan} - \sigma_{\text{dateReturned} \geq \text{dateOut}}(\text{Loan})) \bowtie \text{Student})\big)$
f. $\Pi_{\text{studentNo}}\big(\text{Loan})$
g. $\Pi_{\text{studentNo, equipNo}}(\text{Loan}) \div \Pi_{\text{equipNo}}(\sigma_{\text{category = VR}}(\text{Equipment}))$

**Part 2**
Relational algebra evaluation and reasoning. Using the database instance above, show the resulting relation for each expression. For each answer, show the intermediate relation produced after each major operator and write one short sentence explaining why that operator is used.

a. $\sigma_{\text{category = Vision} \,\land\, \text{dailyRate} \leq 20}(\text{Equipment})$
	The only column of the $\land$ that resulted with a true match value in both vision and dailyRate was E201.

| equipNo | description  | category | dailyRate | labNo |
| ------- | ------------ | -------- | --------- | ----- |
| E201    | Depth Camera | Vision   | 18        | L02   |

b. $\Pi_{\text{studentNo, description}}(\text{Loan} \bowtie \text{Equipment})$
	First, we take the natural join of *Loan* and *Equipment*, matching based on *equipNo*. Then $\Pi$ filters to display the two relevant columns, *studentNo* and *description*.

| loanNo | equipNo | studentNo | dateOut   | dateDue   | dateReturned | description       | category      | dailyRate | labNo |
| ------ | ------- | --------- | --------- | --------- | ------------ | ----------------- | ------------- | --------- | ----- |
| LN01   | E101    | S101      | 10-Sep-26 | 12-Sep-26 | 12-Sep-26    | VR Headset 01     | VR            | 25        | L01   |
| LN02   | E201    | S102      | 11-Sep-26 | 14-Sep-26 | NULL         | Depth Camera      | Vision        | 18        | L02   |
| LN03   | E301    | S103      | 09-Sep-26 | 13-Sep-26 | 13-Sep-26    | Braille Display   | Accessibility | 12        | L03   |
| LN04   | E102    | S101      | 15-Sep-26 | 18-Sep-26 | NULL         | VR Headset 02     | VR            | 25        | L01   |
| LN05   | E302    | S104      | 12-Sep-26 | 15-Sep-26 | 15-Sep-26    | Haptic Controller | Haptics       | 15        | L04   |
| LN06   | E303    | S103      | 14-Sep-26 | 16-Sep-26 | NULL         | 3D Scanner        | Fabrication   | 20        | L04   |

c. $\Pi_{\text{studentNo, firstName, lastName}}\big(\sigma_{\text{dateReturned = NULL}}(\text{Loan}) \bowtie \text{Student}\big)$
	First, we filter down to the loans that specifically have no return date. Then, we use the natural join to connect *studentNo* to the loans, keeping *firstName*, *lastName*, *program*, and *year*. Finally, we use $\Pi$ to keep just the three relevant terms.

| loanNo | equipNo | studentNo | dateOut   | dateDue   | dateReturned |     |
| ------ | ------- | --------- | --------- | --------- | ------------ | --- |
| LN02   | E201    | S102      | 11-Sep-26 | 14-Sep-26 | NULL         |     |
| LN04   | E102    | S101      | 15-Sep-26 | 18-Sep-26 | NULL         |     |
| LN06   | E303    | S103      | 14-Sep-26 | 16-Sep-26 | NULL         |     |

| loanNo | equipNo | studentNo | dateOut   | dateDue   | dateReturned | firstName | lastName | program           | year |
| ------ | ------- | --------- | --------- | --------- | ------------ | --------- | -------- | ----------------- | ---- |
| LN02   | E201    | S102      | 11-Sep-26 | 14-Sep-26 | NULL         | Ethan     | Wong     | Computing Science | 2    |
| LN04   | E102    | S101      | 15-Sep-26 | 18-Sep-26 | NULL         | Mina      | Choi     | Computing Science | 3    |
| LN06   | E303    | S103      | 14-Sep-26 | 16-Sep-26 | NULL         | Sara      | Patel    | Mathematics       | 3    |
