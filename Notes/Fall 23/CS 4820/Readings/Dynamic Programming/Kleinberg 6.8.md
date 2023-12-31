- Let $G=(V,E)$ be a directed graph and each edge $(i,j)\in E$ has a weight $C_{ij}$
- Given G with weights decide if G has a negative cycle
	- A directed cycle C such that $\sum_{ij\in C}c_{ij}<0$
- If the graph has no negative cycles find a path P from the origin node s to a destination node t with minimum total cost $\sum_{ij\in P}c_{ij}$
- If G has no negative cycles then there is a shortest path from s to t that is simple and has at most n-1 edges
- If $i>0, OPT(i,v)=\min(OPT(i-1,v), min(OPT(i-1, w)+c_{vw}))$
- The shortest path method correctly computes the minimum cost of an s-t path  in any graph that has no negative cycles and runs in $O(n^3)$
- 