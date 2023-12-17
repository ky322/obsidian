[[3. Stable Matching and Greedy]]
### Interval Scheduling Problem
- We have a set of $\{1,2,\cdots, n\}$ where $i^{th}$ request corresponds to an interval of time starting at $s(i)$ and finishing at $f(i)$
- A subset of requests is compatible if no two of them overlap in time
- Our goal is to accept as large a compatible subset as possible
- Compatible sets of maximum size is called optimal
### Designing a Greedy Algorithm
- First use a simple rule to select a first request $i_1$
- Once $i_1$ is accepted, we rejected all requests that are not compatible with $i_1$
- We select the next request $i_2$ and reject all requests that are not compatible with $i_2$
- We continue until we run out of requests
- Ideas for Rules
	- Always select the available request that starts the earliest; one with minimal start time $s(i)$
		- Does not always yield an optimal solution 
		- If the earliest request $i$ is for a very long interval then accepting request $i$ we reject a lot of requests for shorter time intervals
		- Our goal is to satisfy as many requests as possible so we end up with a suboptimal solution
	- For each request count the number of other requests that are not compatible and accept the request that has the fewest number of noncompatible requests; select the interval with the fewest conflicts
- Accept the first request that finishes first; the request $i$ for which $f(i)$ is the smallest
```
Initally let R be the set of all requests, let A be empty
While R is not empty
	Choose a request i in R that has the smallest finishing time
	Add request i to A
	Delete all requests from R that are not compatible with request i
Return the set A as the set of accepted requests
```
### Analyzing the Algorithm
- $A$ is a compatible set of requests
	- Let $O$ be an optimal set of intervals. Show $|A|=|O|$
	- Let $i_1,\cdots, i_k$ be the set of requests in $A$ in the order they were added to $A$, $|A|=k$
	- Let $j_1,\cdots, j_m$ be the set of requests in $O$. Show $k=m$
	- Our greedy rule guarantees that $f(i_1)\leq f(j_1)$
	- For each $r\geq1$ the $r^{th}$ accepted request in the algorithm's schedule finishes no later than the $r^{th}$ request in the optimal schedule
- For all indices $r\leq k$ $f(i_r)\leq f(j_r)$
	- By induction, For $r=1$ this is true because the algorithm starts by selecting the request $i_1$ with the minimum finish time
	- Let $r>1$. The statement is true for $r-1$ and we prove it for $r$. From induction we assume $f(i_{r-1})\leq f(j_{r-1})$
	- The greedy algorithm always has the option of choosing $j_r$
	- $O$ consists of compatible intervals so $f(j_{r-1})\leq s(j_r)$ and from our induction hypothesis we get $f(i_{r-1})\leq s(j_r)$
	- Thus the interval $j_r$ is in the set $R$ of available intervals at the time when the greedy algorithm chooses $i_r$
	- The greedy algorithm selects the available interval with the smallest finish time and since interval $j_r$ is one of the available intervals $f(i_{r})\leq f(j_r)$
- The greedy algorithm remains ahead of $O$; for each $r$ the $r^{th}$ interval it selects finishes at least as soon as the $r^{th}$ interval in $O$
- The greedy algorithm returns an optimal set $A$
	- If $A$ is not optimal then an optimal set $O$ must have more requests, $m>k$
	- Applying the previous step with $r=k$ we  get $f(i_k)\leq f(j_k)$
	- $m>k$ so there is a request $j_{k+1}$ in $O$; this request starts after $j_k$ ends and after $i_k$ ends
	- After deleting all the requests that are not compatible with requests $i_1,\cdots,i_k$ the set of possible requests in $R$ still contains $j_{k+1}$
	- The greedy algorithm stops with $i_k$ and only stops when $R$ is empty; a contradiction
### Implementation and Running Time
- Runtime: $O(nlogn)$
	- We sort the $n$ requests in order of finishing time and labeling them in this order taking $O(nlogn)$
		- Assume $f(i)\leq f(j)$ when $i<j$
	- We construct an array $S[1\cdots n]$ where $S[i]$ contains $s(i)$ in $O(n)$ time
- We select requests by processing the intervals in order of increasing $f(i)$ in $O(n)$ time
	- We always select the first interval then iterate through the intervals in order until we reach the first interval $j$ where $s(j)\geq f(1)$ and select this one too
	- If the most recent interval we selected ends at time $f$ we continue iterating through the subsequent intervals until we reach the first $j$ where $s(j)\geq f$
	- We implement in one pass through the intervals, spending constant time per interval 