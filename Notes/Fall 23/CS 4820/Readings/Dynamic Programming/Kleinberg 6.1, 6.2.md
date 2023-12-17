- Goal: Choose a subset $S\subseteq \{1,\cdots,n\}$ to maximize the sum of the values of the selected intervals 
- If $n\in O$ then $O$ must include the optimal solution of requests $S\subseteq \{1,\cdots,n\}$ because then we can replace $O$'s request from $S\subseteq \{1,\cdots,p(n)\}$ with better one
- If $n\notin O$ then ) is equal to the optimal solution to the problem of requests $S\subseteq \{1,\cdots,n-1\}$
- $OPT(j)=max(v_j+OPT(p(j)), OPT(j-1))$
- Request $j$ belongs to an optimal solution on the set $S\subseteq \{1,\cdots,j\}$ if and only if $v_j+OPT(p(j))\geq OPT(j-1)$
- $ComputeOPT(j)$ correctly returns $OPT(j)$ for each $j=1,2,\cdots,n$
	- $OPT(0)=0$. For some $j>0$ and $ComputeOPT(j)$ computes $OPT(i)$ for all $i<j$. By induction hypothesis $ComputeOPT(p(j))=OPT(p(j))$ and  $ComputeOPT(j-1)=OPT(j-1)$ 
### Memorizing the Recursion
- We store the value of $ComputeOPT$ in a globally accessible place and use the precomputed value in place of all future calls
- Use an array $M[0\cdots n]$ and $M[j]$ will be empty initially but then hold the value of $ComputeOPT[j]$ 
- The running time is $O(n)$
	- The time in the single calls is $O(1)$. $M$ has only $n+1$ entries giving $O(n)$ calls
- $j$ belongs to an optimal solution for the set of $\{1,\cdots,n\}$ if and only if $v_j+OPT(p(j))\geq OPT(j-1)$ so we trace back through the array $M$ to find the set of intervals in an optimal solution
- It calls itself recursively only on smaller values for $O(n)$ calls and spends constant time per call
- Given an array $M$ of the optimal values in the sub-problems, we return an optimal solution in $O(n)$ time
### Chapter 6.2
### Designing the Algorithm
- $M[n]$ contains the value of optimal solution on the full instance and we can find the solution by trace back through $M$ to return the optimal solution
- We can directly compute the entries in $M$ by an iterative algorithm instead of memorized recursion
- Start with $M[0]=0$ and increment $j$
### Analyzing the Algorithm
- We prove by induction on $j$ that this algorithm writes $OPT(j)$ in array entry $M[j]$
- Iterative computation is $O(n)$ because it runs for $n$ iterations and spends constant time in each
### Takeaways
1. There are only a polynomial number of subproblems
2. The solution to the original problem can be computed from the solutions to the subproblem
3. There is a natural ordering on the subproblems from smallest to largest together with an easy to compute recurrence that allows one to determine the solutions to a subproblem from the solutions to some number of smaller subproblems
