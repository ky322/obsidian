### Project Selection
-  We have a set $P$ of projects and each project $i\in P$ has a revenue $p_i$
- Certain projects are prerequisites for other projects with a directed acyclic graph $G=(P,E)$
	- Nodes of $G$ are projects; edges $(i,j)$ to show project $i$ can be selected only if $j$ is selected
- A set of projects $A\subseteq P$ is feasible if the prerequisite of every project in A also belongs in A; for each $i\in A, (i,j)\in E, j\in A$ then $\text{profit(A)}=\sum_{i\in A}p_i$
- Goal: Select a feasible set of projects with maximum profit
### Designing the Algorithm
- Project selection problem can be reduced to a minimum cut computation on an extended graph $G'$
- Construct $G'$ from $G$ so the source side of a minimum cut in $G'$ correspond to an optimal set of projects to select
- To form graph $G'$ we add a new source s and sink t to the graph $G$
	- For each node $i\in P, p_i>0$ add an edge $(s,i)$ of capacity $p_i$
	- For each node $i\in P, p_i<0$ add an edge $(i,t)$ of capacity $-p_i$
	- The maximum flow value of this network is at most $C$
- We ensure that if $(A',B')$ is a minimum cut in the graph then $A=A'-\{s\}$ obeys that if node $i\in A$ has edge $(i,j)\in E$ then $j\in A$; we give each edge in $G$ capacity $\infty$
- The maximum possible flow value in $G'$ is a most $C$ so no minimum cut can contain an edge with capacity above $C$
### Analyzing the Algorithm
- Consider a set of projects A where $A'=A\cup\{s\}$ and $B'=(P-A)\cup\{t\}$ and s-t cut $(A',B')$
- No edge $(i,j)$ can crosses this cut so the capacity of the cut $(A',B')$ is $c(A',B')=C-\sum_{i\in A}p_i$
	- The edges of $G'$ can be divided into 3 categories: those corresponding to the edge set E of G, those leaving the source and those entering the sink
	- A satisfies the precedence constraints so the edges in E do not cross the cut $(A',B')$ and do not contribute to capacity
- If $(A',B')$ is a minimum cut in G' then the set $A=A'-\{s\}$ is an optimum solution to the Project Selection Problem
