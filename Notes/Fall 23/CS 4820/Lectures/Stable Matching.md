Algorithms: Learn to recognize how to solve problems quickly or show that this is not possible

## Stable Matching Problem
Assumptions on input:
- $|H|=|R|=n$
- Preference orders are complete and have no ties
- Each hospital requires one resident and each resident wants to be matched to one hospital

A matching $M$ is a set of ordered pairs $(h,r)$ with $h\in H, r\in R$ such that each hospital $h\in H$ and each resident $r\in R$ occurs in at most one pair

A perfect matching $M$ is a matching with $|M|=n$

Given a perfect matching $M$ an instability is a pair $(h,r)$ with $h\in H, r\in R$ such that 
1. $h$ prefers $r$ to its match in $M$
2. $r$ prefers $h$ to its match in $M$

A stable matching is a perfect matching without instabilities

## Gale-Shapley Algorithm

```
M <- Non 0 
while there exists an unmatched hospital
	h <- unmatched hospital
	r <- first resident on h's preferences list that h has not proposed to
	h proposes to r
	if r is unmatched
		add (h,r) to M
	else if r is matched to h'
		if r prefers h to h'
			remove (h', r) from M
			add (h, r) to M
		else
			do nothing
		end if
	end if
end while
Return M

```
