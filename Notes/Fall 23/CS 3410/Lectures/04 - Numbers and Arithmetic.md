### Sign Magnitude Representation
- 1 bit for sign (0 = positive, 1 = negative)
- N - 1 bits for magnitude
- Problem: +0 different from -0

### Two's Complement Representation
- Leading 1's for negative numbers
- To negate any number
	- Complement all the bits (flip the bits)
	- Add 1
- Signed Two's Complement
	- Negative numbers have leading 1s
	- Zero is unique +0 = -0
	- Wraps from largest positive to largest negative
- N Bits can be used to represent
	- Unsigned: range $0\cdots2^{N} - 1$
	- Signed Two's Complement $-(2^{N-1}),\cdots,(2^{N-1}-1)$
- Addition
	- Works as usual just ignore the sign

### Sign Extension and Truncation
- Extending to larger size
	- 1111 = 1111 1111 = -1
- Truncating to smaller size
	- 0000 1111 = 15
	- 1111 = 1111 = -1

### Overflow
- Adding two positives or two negatives
- Occurs when MSB's carry in != carry out

### Binary Subtraction
- Two's Complement Subtraction
	- Inverting all bits and adding one
	- (A-B) = A + (-B) = A+($\bar{B}$ + 1)

