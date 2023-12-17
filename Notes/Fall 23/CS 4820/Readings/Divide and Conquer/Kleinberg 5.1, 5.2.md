- Divide the input into two pieces of equal sizes. Solve the two subproblems on these pieces separately by recursion. Combine the two results into an overall solution spending only linear time for the initial divisions and final recombining
- Let $T(n)$ be the worst case running time on input instances of size n.
- For some constant c $T(n)\leq 2T(n/2)+cn$ when $n>2, T(2)\leq c$
- Any function $T(\cdot)$ satisfying $T(n)\leq 2T(n/2)+cn$ is bounded by $O(nlogn), n>1$
### Chapter 5.2
- For some constant c $T(n)\leq qT(n/2)+cn$ when $n>2, T(2)\leq c$
- Any function $T(\cdot)$ satisfying $T(n)\leq qT(n/2)+cn$ is bounded by $O(n^{log_2q}), q>1$
- Any function $T(\cdot)$ satisfying $T(n)\leq qT(n/2)+cn$ is bounded by $O(n), q=1$
- Any function $T(\cdot)$ satisfying $T(n)\leq qT(n/2)+cn$ is bounded by $O(nlogn), q=2$
- $T(n)\leq 2T(n/2)+cn^2=O(n^2)$
### Review
- $T(n)\leq qT(n/p)+O(n)$
	- $q<p\rightarrow O(n)$
	- $q=p O(nlogn)$
	- $q>p\rightarrow O(n^{log_pq})$
	- 