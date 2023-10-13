### Chapter 2.4
- For any two events A and B with $P(B)>0$ the conditional probability of A given that B has occurred is defined by $$P(A|B)=\frac{P(A\cap B)}{P(B)}, P(A\cap B)=P(A|B)P(B)$$
- The Law of Total Probability: Let $A_1,\cdots, A_k$ be mutually exclusive and exhaustive events. Then for any other event B $$P(B)=P(B|A_1)P(A_1)+\cdots+P(B|A_k)P(A_k)=\sum_{i=1}^kP(B|A_i)P(A_i)$$
- Bayes Theorem: Let $A_1,\cdots, A_k$ be a collection of $k$ mutually exclusive and exhaustive events with prior probabilities $P(A_i)$ Then for any other event B for which $P(B)>0$ the posterior probability of $A_j$ given that B has occurred is $$P(A_j|B)=\frac{P(A_j\cap B)}{P(B)}=\frac{P(B|A_j)P(A_j)}{\sum_{i=1}^kP(B|A_i)P(A_i)}$$
### Chapter 2.5
- Two events are independent if $$P(A|B) = P(A)$$
- A and B are independent if and only if $$P(A\cap B)=P(A)P(B)$$
- Events $A_1,c\dots,A_n$ are mutually independent if for every $k$ and every subset of indices $$P(A_1\cap\cdots\cap A_k)=P(A_1)\times\cdots\times P(A_k)$$