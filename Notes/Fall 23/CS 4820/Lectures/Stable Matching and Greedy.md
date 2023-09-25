We showed:
1. G-S algorithm outputs a stable matching in $O(n^2)$ time
2. No hospital ever gets rejected by a valid partner

#### Conclusion
G-S algorithm always find the same stable matching in which each hospital gets their preferred valid partner. "G-S algorithm finds the hospital-optimal stable matching"
#### Claim
The output of the G-S algorithm matches each resident to their worst valid partner (resident-pessimal)
#### Proof
Let $M$ be the output of the G-S algorithm. Suppose $(h,r)\in M$ such that $h$ is not the worst valid partner for $r$. 
Let $h'$ be the worst valid partner for $r$. 
Let $M'$ be the stable matching containing $(h',r)$. 
Let $r'$ be the match for $h$ is $M'$
We will argue that $(h, r)$ is an instability for $M'$
- $r$ prefers $h$ to $h'$ because $h'$ is their worst valid partner and $h$ is also a valid partner
- $h$ prefers $r$ to $r'$ because $h$ is matched to $r$ in the G-S algorithm so $r$ is $h's$ best valid partner
$\rightarrow$ Because $M'$ has an instability, we contradicted that $M'$ is stable

## Greedy Algorithms
### Interval Scheduling Problem
Input: $n$ jobs (intervals); each job $j$ is an interval $[s(j), f(j)]$
Goal: Accept a set of non-overlapping jobs that is as large as possible
### Generic Greedy Algorithm
```
Initalize R <- {1,2,...,n}, A <- Non-Zero
while R != 0
	choose j* in R (by greedy rule)
	add j* to A
	remove from R all jobs that overlap j*
end while
return A
```
Two greedy rules that are guaranteed to give an optimal (maximum cardinality) set of non-overlapping jobs
1. Select job in $R$ that finishes first (minimizing $f(j)$)
2. Select job in $R$ that starts last (maximizing $s(j)$)
#### The Earliest Finish Time (EFT) Algorithm
- Choose $j*$ that minimizes $f(j)$ among jobs $j$ in $R$
- $j*=\text{argmin}_{j\in R}f(j)$

#### Correctness
WTS: EFT algorithm returns an optimal (max size) set of non-overlapping jobs
#### Proof Strategy: Greedy-Stays-Ahead
- Proof by induction on number steps by the greedy algorithm
- Argues that the algorithm's solution $A$ up to $k$ steps is at least good as any other solution $O$ up to $k$ steps.

