### Polynomial Time Reduction
- Problem X is at least as hard as problem Y
- Can arbitrary instances of problem Y be solved sing a polynomial number of computational steps plus a polynomial number of calls to a black box that solves problem X
	- If yes then $Y\leq_p X$ and suppose $Y\leq_p X$. If $X$ can be solved in polynomial time then $Y$ can be solved in polynomial time
### Independent Set and Vertex Cover
- Given a graph G and a number k does G contain an independent set of size at least k?
	- If we solve the decision version of Independent set for each k then we find the maximum independent set
- Given a graph G and a number k does G contain a vertex cover of size at most k?
	- A set of nodes $S\subseteq V$ is a vertex cover if every edge $e\in E$ has at least one end in $S$
- We show Vertex Cover $\leq_p$ Independent Set and Independent Set $\leq_p$ Vertex Cover
- Let $G=(V,E)$ Then S is an independent set if and only if its complement V-S is a vertex cover
	- Suppose S is an independent set and consider $e=(u,v)$. If S is independent then both u and v cannot be in S so one must be in V-S. Every edge has at least one end in V-S so V-S is a vertex cover
	- Suppose V-S is a vertex cover. Consider nodes u and v in S. If they are joined by e then neither end of e would lie in V-S contradicting our assumption. No two nodes in S are joined by an edge so S is an independent set
-  Independent Set $\leq_p$ Vertex Cover
	- If we have a black box to solve Vertex Cover, we can decide if G has an independent set of size at least k by asking if G has a vertex cover of size at most n-k
- Vertex Cover $\leq_p$ Independent Set
	- If we have a black box to solve Independent Set we can decide if G has a vertex cover of size at most k by asking the box whether G has an independent set of size n-k
- Set Cover: Given a set U of n elements, a collection of subsets of U, and a number k does there exist a collection of at most k of these sets whose union is equal to all of U?
- Set Packing Problem: Given a set U of n elements, a collection of subsets of U and a number k does there exists a collection of at least k of these sets with the property that no two of them intersect?