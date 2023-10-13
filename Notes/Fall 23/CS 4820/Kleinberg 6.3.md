- Given a sequence of data points we want to identify a few points in the sequence at which a discrete change occurs

### Formulating the Problem
- We are given a set of $P=\{(x_1,y_1),\cdots,(x_n,y_n)\}$ and we partition $P$ into segments. For each segment $S$ in $P$ we compute the line minimizing the error with respect to points in $S$
- The penalty of the partition is the sum of
	1. The number of segments into which we partition $P$ times $C$
	2. For each segment the error value of the optimal line through the segment
- Goal: Find a partition of minimum penalty

### Designing the Algorithm
- We want a polynomial number of subproblems and build these subproblems using a reoccurrence
- The last point $p_n$ belongs to a single segment in the optimal partition and the segment begins at some earlier point $p_i$
- If we knew the identity of the last segment then we can remove those points from consideration and recursively solve the problem on the remaining points $p_1,\cdots,p_{i-1}$
- Suppose $OPT(i)$ is the optimal solution for the points $p_1,\cdots,p_i$ and $e_{i, j}$ is the minimum error of any line
- If the last segment of the optimal partition is $p_1,\cdots,p_n$ then the value of the optimal solution is $OPT(n)=e_{i,n}+C+OPT(i-1)$
- For the subproblem on the points $p_1,\cdots,p_j$ $OPT(j)=min(e_{i,j}+C+OPT(i-1))$ and the segment used in an optimum solution for the subproblem if and only if the minimum is obtained using index $i$

### Analyzing the Algorithm
- To calculate the $e_{i,j}$ there are $O(n^2)$ pairs and for each pair $(i,j)$ we compute $e_{i,j}$ in $O(n)$ time so computing $e_{i,j}$ is $O(n^3)$
- The algorithm has $n$ iterations for values $j=1,\cdots,n$ For each value of $j$ we determine the minimum in the recurrence to fill the array entry $M[j]$ taking $O(n)$ for each j for total $O(n^2)$
- The run time is $O(n^2)$  once all the $e_{i,j}$ is determined
- 