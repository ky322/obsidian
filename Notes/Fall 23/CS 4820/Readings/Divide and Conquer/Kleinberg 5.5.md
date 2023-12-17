### Multiplying Integers
- Break up product into partial sums $xy=x_1y_12^n+(x_1y_0+x_0y_1)2^{n/2}+x_0y_0$
- Recursively compute the results of these four n/2 bit instances and combine them taking $O(n)$
- $T(n)\leq4T(n/2)+cn\rightarrow O(n^2)$
- We can try to get 3 recursive calls (with algebra)
- $T(n)\leq3T(n/2)+cn\rightarrow O(n^{1.59})$
- The running time of Recursive-Multiply (Karatsuba) on two n-bit factors is $O(n^{1.59})$
