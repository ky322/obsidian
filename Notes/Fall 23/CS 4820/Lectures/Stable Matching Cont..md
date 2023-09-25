A matching $M$ is a stable matching if it is perfect and has no instabilities

## Gale-Shapley Algorithm
### Analysis
#### Running Time
WTS: The running time of the Gale-Shapley algorithm is bounded by $O(n^2)$
1. Number of iterations (proposals) is $\leq n^2$
2. Each iteration can be implemented to run in $O(1)$ time
#### Correctness
WTS: The Gale-Shapley algorithm outputs a stable matching

Let $M$ be the output of the algorithm. By the description of the algorithm, $M$ is perfect. Suppose $M$ has an instability $(h, r)$. Let $(h, r')\in M$ and $(h', r)\in M$; then $(h, r)$ is an instability means $h$ prefers $r$ to $r'$ and $r$ prefers $h$ to $h'$
Since $h$ prefers $r$ to $r'$, we know $h$ proposed to $r$ before proposing to $r'$ so $r$ must have rejected $h$ at some point because they had a better match. By Useful Observation $r$ prefers $h'$ to $h$ so $(h, r)$
is not an instability
#### Useful Observation
Once a resident is matched, they stay matched and can only improve the hospital they are matched to
For a hospital that means they can get rejected at most $n-1$ times (because $|R|=|H|=n$)
Each hospital makes at most $n$ proposals

Next, we will show G-S algorithm always find the same stable matching regardless of the order in which we allowed hospitals to propose

We will call $(h, r)$ a valid match if there exists a stable matching containing $(h, r)$. We will also say $h$ and $r$ are valid partners in this case.
#### Claim
No hospital ever gets rejected by a valid partner

The claim implies that at the end of the G-S algorithm, each hospital is matched to their most preferred valid partner

#### Proof of Claim
By contradiction, consider the first time in the algorithm's execution that a hospital gets rejected by a valid partner. Call this hospital $h$, the resident $r$, and let $M$ be a stable matching with $(h, r)\in M$. $M$ exists because $h, r$ are valid partners.

$r$ rejects $h$ because they are currently matched to a hospital $h'$ that they prefer to $h$
$h'$ must be matched in $M$ to some resident $r'$. We consider two possibilities:
1. $h'$ prefers $r$ to $r'$. Then $(h', r)$ is an instability for $M$, contradicting that $M$ is stable
2. $h'$ prefers $r'$ to $r$. The fact that $h'$ is currently matched to $r$ in the algorithm means that $r'$ rejected $h'$ earlier, but $h'$ and $r'$ are valid partners, so this contradicts the fact that we're looking at the first time a hospital gets rejected by a valid partner.
We derived a contradiction in each case, so no hospital ever gets rejected by a valid partner
