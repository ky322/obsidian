### Logic Implementation
- How to implement a desired logic function
	1. Write the minterms
	2. Write the sum of products or of all minterms where out = 1
- Any combinational circuit can be implemented in two levels of logic

### Bubble Pushing
- (X') = X
- (X+Y+Z)' = X'Y'Z'
	- Push bubble through the gat and change the gate

### Karnaugh Maps
- Sum of minterms yield: out = $\bar{ab}c + \bar{a}bc + a\bar{bc} + a\bar{b}c$
- K-maps identify which inputs are relevant to the output
- Minimization with K-Maps
	- Circle 1s
	- Each circle is a logical component of the final equation
	- Circles cover only 1s
	- Circles span rectangles of size power of 2 (1,2,4,8)
	- Use fewest circles necessary to cover all 1s (be as large as possible)
	- Circles may wrap around edges of K-Map
	- Overlaps okay if that means fewer circles
	- 