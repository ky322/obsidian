[[1. Stable Matching]]
[[2. Stable Matching Cont.]]
- Given a set of preferences among employers and applicants, can we assign applicants to employers so that for every employer E and every applicant A who is not scheduled to work for E at least one of the following is the case
	1. E prefers every one of its accepted applicants to A
	2. A prefers her current situation over working for employer E
If this holds then the outcome is stable and individual self-interests will prevent any applicant or employer deal from being made behind the scenes
### Formulating the Problem
- Consider a set $M=\{m_1,\cdots, m_n\}$ of n men and a set $W=\{w_1,\cdots, w_n\}$ of n women. Let $M\times W$denote the set of all possible ordered pairs of the form $(m,w)$ where $m\in M$ and $w\in W$
- A matching set $S$ is a set of ordered pairs each from $M\times W$ and that each member of M and W appears in at most one pair in $S$.
- A perfect matching $S'$ is a matching that each member of M and W appears in one pair in only $S'$
- Each man $m\in M$ ranks all the women; $m$ prefers $w$ to $w'$ if $m$ ranks $w$ higher than $w'$
- A pair $(m, w')$ is an instability with respect to $S$; $(m, w')$ does not belong to $S$ but each of $m$ and $w'$ prefers the other to their partner in $S$
- A matching $S$ is stable if it is perfect and there is no instability with respect to $S$
### Designing the Algorithm
```
Initially all m in M and w in W are free
While there is a man w who is free and has not proposed to every woman
	Choose such a man m
	Let w be the highest ranked woman in m's pref list that m has not yet proposed
	If w is free then
		(m, w) become engaged
	Else w is currently engaged to m;
		If w prefers m' to m then
			m reamins free
		Else w prefers m to m;
			(m, w) become engaged
			m' becomes free
Return set of S of engaged pairs
```
### Analyzing the Algorithm
- $w$ remains engaged from the point at which she receives her first proposal; and the sequence of partners to which she is engaged gets better and better in terms of preference list
- The sequence of women to whom $m$ proposes gets worse and worse in terms of his preference list
- The G-S algorithm ends after at most $n^2$ iterations of the while loop
	- Each iteration consists of some man proposing for the only time to a woman he has never proposed to before.
	- Let $P(t)$ denote the set of pairs $(m, w)$ such that $m$ proposed to $w$ by the end of iteration $t$ we see that for all $t$ the size of $P(t+1)$ is strictly greater than the size of $P(t)$
	- There are only $n^2$ possible pairs of men and women so the value of $P(t)$ can increase at most $n^2$ times over the course of the algorithm 
	- There can be at most $n^2$ iterations
- The set $S$ returned at the end of the algorithm is a perfect matching. We show that no man can fall off the end of his preference list; the only way for the while loop to end is for there to be no free man so the set of engaged couples would be a perfect matching
- If $m$ is free at some point in the algorithm then there is a woman to whom he has not yet proposed
	- Suppose $m$ is free but has proposed to every woman. Then by "$w$ remains engaged from the point at which she receives her first proposal; and the sequence of partners to which she is engaged gets better and better in terms of preference list" each of the $n$ women is engaged. 
	- The set of engaged pairs forms a matching, there must also be $n$ engaged men but there are only $n$ men total and $m$ is not engaged so this is a contradiction
- The set $S$ returned at termination is a perfect matching
	- The set of engaged pairs always forms a matching. Suppose the algorithm terminated with a free man $m$. At termination it must be the case that $m$ proposed to every woman.
	- This contradicts "If $m$ is free at some point in the algorithm then there is a woman to whom he has not yet proposed" 
- Consider an execution of the G-S algorithm that returns a set of pairs $S$. The set $S$ is a stable matching
	- $S$ is a perfect matching. To prove $S$ is a stable matching assume that there is an instability with respect to $S$ to get a contradiction where $m$ prefers $w'$ to $w$ and $w'$ prefers $m$ to $m'$
	- In the execution of the algorithm that produced $S$, by definition $m$ last proposal was to $w$
	- If $m$ proposed to $w'$ earlier in the execution then he was rejected by $w'$ in favor or some other than $m''$ whom $w'$ prefers to $m$
		- $m'$ is the final partner of $w'$ so $m''=m'$ or $w'$ prefers $m'$ to $m''$
	- Otherwise he did not prose to $w'$ earlier
		- $w$ must be higher on $m$ preference list than $w'$ contradicting the assumption that $m$ prefers $w'$ to $w$
### Extensions
- All executions yield the same matching
	- $w$ is a valid partner of $m$ if there is a stable matching that contains the pair $(m,w)$.
	- $w$ is the best valid partner of $m$ if $w$ is a valid partner of $m$ and no woman whom $m$ ranks higher than $w$ is a valid partner of his
	- Let $S^*$ denote the set of pairs $\{(m,\text{best}(m)):m\in M\}$
- Every execution of the G-S algorithm results in the set $S^*$
	- Suppose that some execution of $E$ of the G-S algorithm results in a matching $S$ in which some man is paired with a woman who is not his best valid partner
	- Men propose in decreasing order of preference so some man is rejected by a valid partner during the execution $E$ of the algorithm
	- In the moment during the $E$ in which some man $m$ is rejected by a valid partner $w$
		- It must be that $w$ is $m$ best valid partner $\text{best}(m)$
		- $w$ forms or continues an engagement with a man $m'$ whom she prefers to $m$
	- $w$ is a valid partner of $m$ so there exists a stable matching $S'$ containing $(m, w)$
	- The rejection of $m$ by $w$ was the first rejection of a man by a valid partner in $E$ so $m'$ had not been rejected by any valid partner in $E$ when he became engaged to $w$
	- He proposed in decreasing order of preference and $w'$ is a valid parter of $m'$ so $m'$ prefers $w$ to $w'$
	- We know $w$ prefers $m'$ to $m$ because she rejected $m$ for $m'$
	- $(m',w)\notin S'$ so $(m',w)$ is an instability in S'
	- This contradicts our claim that $S'$ is stable and contradicts our assumption
- In the stable matching $S^*$ each woman is paired with her worst valid partner
	- Suppose there were a pair $(m, w)$ in $S^*$ such that $m$ is not the worst valid partner of $w$. 
	- There is a stable matching $S'$ in which $w$ is paired with a man $m'$ whom she likes less than $m$
	- In $S'$ $m$ is paired with a woman $w'\neq w$ because $w$ is the best valid partner of $m$ and $w'$ is a valid partner of $m$ but $m$ prefers $w$ to $w'$
	- $(m, w)$ is an instability in $S'$ contradicting the claim $S'$ is stable 
- For any input the side that does the proposing in the G-S algorithm ends up with the best possible stable matching and the side that does not do the proposing ends up with the worst possible stable matching