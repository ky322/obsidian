### The Problem
- We have n items $\{1,...,n\}$ with a nonnegative weight $w_i$ and want to choose a subset S of the items so that $\sum_{i\in S}w_i\leq W$
- Recurrence: If $w<w_i$ $OPT(i,w)=OPT(i-1,w)$ 
	- Else $OPT(i,w)=\max OPT(i-1,w), w_i+OPT(i-1,w-w_i)$
- The Subset Sum(n, w) algorithm correctly computes the optimal value of the problem and runs in $O(nW)$ time
- Given a table $M$ of the optimal values of the subproblems the optimal set S can b e found in $O(n)$ time