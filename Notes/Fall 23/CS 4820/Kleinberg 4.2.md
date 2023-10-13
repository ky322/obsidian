- We have a single resource and a set of $n$ requests to use the resource for an interval of time
- The request $i$ has a deadline $d_i$ and has length $t_i$
- At start $s$ we assign each request $i$ an interval $[s(i),f(i)]$ where $f(i)=s(i)+t_i$
- $i$ is late if $f(i)>d_i$ and lateness is $l_i=f(i)-d_i$ $l_i=0$ if not late
- Schedule all requests with nonoverlapping intervals to minimize maximum lateness $L=max_il_i$

### Designing The Algorithm
- Sort the jobs in increasing order of their deadlines $d_i$ and schedule them in this order
```
Order the jobs ini order of their deadlines
Assume d1 <= ... <= dn
f=s
Consider the jobs i = 1,..., n in this order
	Assign job i to the time interval from s(i) = f to f(i) = f + ti
	Let f = f + ti
Return the set of scheduled intervals [s(i), f(i)] for i = 1,...,n 
```
### Analyzing the Algorithm
- There is an optimal schedule with no idle time
- Schedule $A'$ has in inversion if a job $i$ with deadline $d_i$ is scheduled before job $j$ with deadline $d_j<d_i$
- All schedules with no inversions and no idle time have the same maximum lateness
	- They only differ in the order in which jobs with identical deadlines are scheduled
	- For a deadline $d$, in both schedules jobs with $d$ are scheduled consecutively
	- Among the jobs with $d$ the last one has the greatest deadline and this lateness does not depend on the order of the jobs
- There is an optimal schedule with no inversions and no idle time
	- There is an optimal schedule $O$ with no idle time
	- If $O$ has in inversion then there is a pair of jobs $i$ and $j$ such that $j$ is scheduled immediately after $i$ and has $d_j < d_i$
		- Consider an inversion where job $a$ is scheduled before job $b$ and $d_a>d_b$
		- There is a point at which the deadline decreases for the first time
		- This corresponds to a pair of consecutive jobs that form an inversion
		- Suppose $O$ has at least one inversion and let $i$ and $j$ be a pair of inverted requests that are consecutive in the scheduled order
		- We will decrease the number of inversions in $O$ by swapping $i$ and $j$ in $O$
		- The pair $(i, j)$ formed an inversion in $O$ and is eliminated with the swap and creates no new inversions
- After swapping $i$ and $j$ we have a schedule with one less inversion
- The new swapped schedule has a maximum lateness no larger than that of $O$
	- $O$ can have at most $\binom{n}{2}$ inversions and after $\binom{n}{2}$ swaps we have an optimal schedule with no inversions
	- By swapping a pair of consecutive, inverted jobs we do not increase the maximum $L$
	- The finishing time of $j$ before the sap is equal to the finishing time of $i$ after the swap
	- All jobs other than $i$ and $j$ finish at the same time in the two schedules
	- $j$ will be finished earlier in the new schedule so the swap does not increase the lateness of $j$
	- After the swap $i$ finishes at time $f(j)$ when $j$ finishes in $O$
	- If $i$ is late in this new schedule its lateness is $\bar{l_i}=\bar{f(i)}-d_i=f(j)-d_i$
	- $i$ cannot be more late in $\bar{O}$ than $j$ was in $O$ because our assumption $d_i>d_j$ implies that $\bar{l_i}=f(j)-d_i<f(j)=d_j=l'_j$
	- The lateness of $O$ was $L'\geq l'_j>\bar{l'_j}$ so the swap does not increase the maximum lateness
- The schedule $A$ produced by the greedy algorithm has optimal maximum lateness $L$
	- We proved that an optimal schedule with no inversions exists and all schedules with no inversions have the same maximum lateness so the schedule obtained by the greedy algorithm is optimal