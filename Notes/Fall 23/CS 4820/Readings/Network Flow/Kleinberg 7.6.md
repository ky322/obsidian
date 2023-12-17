### Disjoint Paths in Directed and Undirected Graphs
- Edge-disjoint paths: If the edge sets are disjoint that no two paths share an edge
- Given a directed or undirected graph $G=(V,E)$ our goal is to find the maximum number of the edge disjoint s-t paths in G
- Directed
	- Given a graph $G=(V,E)$ with s and t and a capacity of 1 on each edge.
	- Suppose there are k edge disjoint s-t paths and set the flow $f(e)=1$ for each edge e on any of the paths and $f(e')=0$ on other paths giving us a flow of value $k$
- If there are k edge disjoint paths in a directed graph $G$ from s to t then the maximum s-t flow in G is at least k
- If there is a flow of at least k then there exist k edge disjoint s-t paths 
	- We then compute a maximum s-t flow in G and declare this as the maximum number of edge disjoint s-t paths
- If $f$ is a 0-1 valued flow of value v then the set of edges with flow value $f(e)=1$ contains a set of v edge disjoint paths
	- Proof by Induction: If $v=0$ then there is nothing to prove
	- Otherwise there must be an edge $(s,u)$ that carries one unit of flow
	- If we reach t then we find a path P from s to t and use this path as one of our v paths
		- Let f' be the flow obtained by decreasing flow values on the edges along P to 0
		- f' has value v-1 and has fewer edges that carry flow
		- We get v-1 edge disjoint paths along path P form the v paths claimed
	- If P reaches a node v for a second time then we decrease flow values on edges along C to 0 so f' has value v but fewer edges than carry flow
- There are k edge disjoint paths in a directed graph G from s to t if and only if the value of the maximum value of an s-t flow in G is at least k
### Running Time
- The FF can be used to find a maximum set of edge disjoint s-t paths in a directed graph G in $O(mn)$ time
- In every directed graph with nodes s and t the maximum number of edge disjoint s-t paths is equal to the minimum number of edges whose removal separates s from t 
	- If the removal of a set $F\subseteq E$ of the edges separates s from t then each set s-t path must use at least one edge from F and the number of edge disjoint s-t paths is at most $|F|$
	- In the other direction by the maximum number of edge is the value v of the maximum s-t flow
	- There is a s-t cut (A,B) with capacity v so let F be the set of edges that go from A to B
	- Each edge has capacity 1 so $|F|=v$ and by definition of s-t cut removing these v edges from G separates s from t
### Disjoint Paths in Undirected Graphs
- We replace each undirected edge $(u,v)$ in G by two directed edges $(u,v)$ and $(v,u)$ and create a directed version G' of G
- In any flow network there is a maximum flow f where for all opposite directed edges e and e' either f(e)=0 or f(e')=0. If the capacities of the flow network are integral then there is such an integral maximum flow
- There are k edge disjoint paths in an undirected graph G from s to t if and only if the maximum value of an s-t flow fin the directed version G' of G is at least k. The FF algorithm can be used to find a maximum set of disjoint paths in an undirected graph in $O(mn)$ time
- In every undirected graph with nodes s and t the maximum number of edge disjoint s-t paths is equal to the minimum number of edges whose removal separates s from t