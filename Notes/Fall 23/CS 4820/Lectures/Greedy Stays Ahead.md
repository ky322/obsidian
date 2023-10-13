### Interval Scheduling Problem
Input: n jobs (interval), each job j is an interval $[s(j), f(j)]$
Goal: Accept a set of non-overlapping jobs that is as large as possible

### Earliest Finish Time Algorithm
```
Initalize R <- {1,2,...,n} A <- empty set
while R != Empty Set
	Choose j* in R (with smallest finish time)
	add j* to A
	remove from R (jobs that overlap j*)
End while
Return A
```

### Correctness
Let $a_k$ be the $kth$ job added to $A$ by the algorithm. Observe that $f(a_k)\leq f(a_{k+1})$ for $k=1,2,\cdots$ Let $O=\{O_1,O_2,\cdots\}$ be another set of non overlapping jobs indexed so that $f(o_k)\leq f(o_{k+1})$ for $k=1,2,\cdots$
Claim: If $a_k$ and $o_k$ both exists $f(a_k)\leq f(o_k)$ for $k=1,2,\cdots$
Proof: By induction on $k$
Base Case: $k=1$ $a_1$ is the job that finishes first among all jobs so $f(a_1)\leq f(o_1)$
Inductive Step: Assume $f(a_k)\leq f(o_k)$. We want to show $f(a_{k+1})\leq f(o_{k+1})$
By induction $f(a_k)\leq f(o_k)$ and $a_{k+1}$ starts after $f(o_k)$ because O is non overlapping, we know $o_{k+1}$ starts after $f(a_k)$ $o_{k+1}$ is one of the jobs the EFT algorithm can choose in step $k+1$. By EFT rule, we therefore know $f(a_{k+1})\leq f(o_{k+1})$
Corollary: $|A|\geq|O|$ for any set of non overlapping jobs $O$
Proof: The set of jobs available as the next job in $O$ is a subset of the jobs available to be the next job in $A$ by the claim above
Running Time: Algorithm has at most n iterations each takes $\leq n$ time $O(n^2)$
Faster Implementation that runs in $O(nlogn)$ time:
```
sort jobs by finish time O(nlogn)
Let A be the set of selected jobs, f the finish time of the last job added to A
Initalize A <- empty set, f <- -10
Go through jobs in order
If s(j) <= f
	j overlaps A so you go to next job
Else:
	j is job with smallest finish time that does not overlap A so we add j to A and update f to f(j)
```

Alternative Proof of Correctness (Minmax Argument)
Let $F_A = \{f(j): j\in A\}$
Observe that each interval in the input contains a point in $F_A$
Taking more than $|F_A|$ intervals can never be a set of non overlapping jobs 
$A$ is optimal

### Scheduling to Minimize Lateness
Input: n jobs, each job j has a processing time $t_j$ and a deadline $d_j$
Goal: Schedule all jobs to minimize the maximum lateness (objective function)
Given a schedule:
- Let $C_j$ = completion time of job j
- Let $L_j$ = Lateness of job j 
=max$\{c_j-d_j,0\}$
Maximum lateness is $L_{max} = max_jL_j$
We want to choose the schedule that minimizes this

### Earliest Deadline (ED) Algorithm
Sort jobs by deadline
#### Running Time: O(nlogn)
#### Correctness (Exchange Argument)
Let A be schedule by ED algorithm and let O be an optimal solution
Prove A is at least as good as O by showing how to do exchanges that
1. Transform O into A
2. Do not make the objective function (max lateness) worse