### Chapter 2.1
Sample Space: The set of all possible outcomes of an experiment
Event: Any collection of outcomes contained in the sample space. 
- Simple: If it consists of exactly one outcome
- Compound if it consists of more than one outcome
1. Complement of an event A, A': The set of all outcomes in S that are not contained in A
2. Union of two events A and B ($A\cup B$): The event consisting of all outcomes that are either in A or in B or in both events; all outcomes in at least one of the events
3. Intersection of two events A and B ($A\cap B$): Event consisting of all outcomes that are in both A and B
Let $\emptyset$ denote the null event; When $A\cap B = \emptyset$ A and B are mutually exclusive or disjoint events
### Chapter 2.2
Axiom
1. For any event A, $P(A) \geq 0$
2. P(S) = 1
3. If $A_1, A_2,\cdots$ is an infinite collection of disjoint events then $$P(A_1\cup A_2\cup\cdots) =\sum_{i=1}^\infty P(A_i)$$
P($\emptyset$) = 0
Sum of Geometric Series: $\frac{a}{1-r}$
- For any event A: $P(A)+ P(A') = 1$ and $P(A) = 1 - P(A')$
- For any event A, $P(A)\leq1$
- For any two events A and B: $P(A\cup B) = P(A)+P(B)-P(A\cap B)$
- For any three events A,B, C $$P(A\cup B \cup C)=P(A)+P(B)+P(C)-P(A \cap B) - P(A \cap C) - P(B \cap C) + P(A \cap B \cap C)$$
- Countability infinite: Outcomes can be listed in an infinite sequence
- Let $E_1, E_2, E_3\cdots$ denote the simple events, each consisting of a single outcome. The probability of any compound event $A$ is computed by adding the $P(E_i)$ for all $E_i$ in A $$P(A)=\sum_{\text{all E in A}}P(E_i)$$
- When the outcomes of an experiment is equally as likely for an event $A$ with $N(A)$ denoting the number of outcomes contained in A $$P(A)= \sum_{\text{E in A}}P(E_i)=\sum_{\text{E in A}}\frac{1}{N}=\frac{N(A)}{N}$$
### Chapter 2.3
- If the first element or object of an ordered pair can be selected in $n_1$ ways and for each of these $n_1$ ways the second element of the pair can be selected in $n_2$ ways then the number of pairs is $n_1n_2$
- Permutation: Ordered subset $$P_{k, n} = \frac{n!}{(n-k)!}$$
- Combination: Unordered subset $$\binom{n}{k}=\frac{P_{k,n}}{k!}=\frac{n!}{k!(n-k)!}$$
- Note $\binom{n}{n}=1,\binom{n}{0} = 1,\binom{n}{1}=n$

