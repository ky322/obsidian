## Transistors 
- N-Type Silicon: Negative free-carriers (electrons)
- P-Type Silicon: Positive free-carriers (holes)
- P-Transistor: Negative charge on gate generates electric field that creates a (+ charged) p-channel connecting source & drain
- N-Transistor: Works the opposite way
- Complementary MOS = CMOS uses both p-type and n-type transistors

## CMOS Notation 

![[cmos-notation.png]]

- Gate input controls whether current can flow between the other two terminals or not
- The "o" bubble of the p-type indicates that this gate wants a $0$ to be turned on

## 2-Transistor Combination: NOT 
- Logic gates are constructed by combining transistors in complementary arrangements
- Combine p&n transistors to make a NOT gate

![[Fall 23/CS 3410/Images/transistor-combination.png]]

## Inverter
![[inverter.png]]

## Logic Gates
- Digital circuit that either allows signal to pass through it or not  
- Used to build logic functions
- Seven basic logic gates: NOT, AND, OR, XOR, NAND, NOR, XNOR
![[Fall 23/CS 3410/Images/logic-gates.png]]

![[Fall 23/CS 3410/Images/nor-gate.png]]

## Universal Gates
- NAND and NOR can implement any function
- Useful for manufacturing 

![[nand-nor.png]]

## Logic Implementation
1. Write minterms
2. Write sum of products or of all minterms where out = 1
Any combinational circuit can be implemented in two levels of logic

![[logic-constructor.png]]

## Logic Symbols & Notation
- NOT = $\bar{a}=!a=\neg a$
- AND = $a\cdot b=a\&b=a\wedge b$
- OR = $a+b = a|b = a\vee b$
- XOR = $a\oplus b = a\bar{b}+\bar{a}b$
