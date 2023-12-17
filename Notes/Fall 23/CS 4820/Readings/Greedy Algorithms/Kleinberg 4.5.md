- Suppose we have a set of locations $\{v_1,\cdots,v_n\}$; for some pairs $(v_i, v_j)$ we build a link between them for a cost $c(v_i, v_j) > 0$
- The set of possible links that can be built is $G=(V,E)$ with a positive cost $c_e$ associated with each edge $e=(v_i,v_j)$
- Find a subset of edges $T\subset E$ so graph $(V,T)$ is connected and total cost is small
- Let $T$ be a minimum cost solution to the network design problem. Then $(V,T)$ is a tree
	- $(V,T)$ must be connected and contain no cycles
	- Suppose it contained a cycle $C$ and let $e$ be any edge on $C$, we claim $(V, T-\{e\})$ is still connected since any path used by $e$ can go the long way of C instead
	- $(V,T-\{e\})$ is a valid solution and is cheaper, a contradiction
- Subset $T\subset E$ is a spanning tree of G if $(V,T)$ is a tree
- Goal: Finding the cheapest spanning tree of the graph
### Designing Algorithms
1. Kruskal's Algorithm: Start without any edges and builds a spanning tree by successively inserting edges from $E$ in order of increasing cost. As we move through the edges in this order we insert $e$ as long as it does not create a cycle when added to the edges we already inserted, otherwise discard and continue
2. Prim's Algorithm: We start with a root node $s$ and greedily grow a tree from $s$ outward. At each step we add the node that can be attached as cheaply as possible to the partial tree we have. We maintain a set $S\subseteq V$ on which a spanning tree has been constructed so far. $S=\{s\}$ In each iteration we grow $S$ by one node, adding the node $v$ that minimizes the attachment cost $min_{e=(u,v):u\in S}c_e$ and including the edge $e=(u,v)$ that achieves the minimum in the spanning tree.
3. Reverse-Delete Algorithm: We start with the full graph $(V,E)$ and delete edges in order of decreasing cost. As we get to each edge $e$ we delete it if it does not disconnect the current graph

### Analyzing the Algorithms
- Cut Property: Assume that all edge costs are distinct. Let $S$ be any subset of nodes that is neither empty nor equal to all of $V$ and let edge $e=(v,w)$ be the minimum cost edge with one end in $S$ and the other in $V-S$. Then every minimum spanning tree contains the edge $e$
	- Let $T$ be a spanning tree that does not contain $e$ so $T$ does not have the minimum possible cost. By exchange argument, let $e'$ be in $T$ that is more expensive than $e$ and exchanging $e$ for $e'$ results in another spanning tree and will be cheaper than $T$
	- To find an edge, the ends of $e$ are $v, w$. $T$ is a spanning tree so there must be a path $P$ in $T$ from $v\rightarrow w$ 
	- Starting at $v$ suppose we follow the nodes of $P$ in sequence. There is a first node $w'$ on $P$ that is in $V-S$. Let $v'\in S$ be the node just before $w'$ on $P$ and let $e'=(v',w')$ be the edge joining them so $e'$ is an edge of $T$ with one end in $S$ and the other in $V-S$
	- If we exchange $e$ for $e'$ we get the set $T'=T-\{e'\}\cup\{e\}$ and $T'$ is a spanning tree so $(V, T')$ is connected because $(V,T)$ is connected and any path in $(V,T)$ that used the edge $e'=(v',w')$ can be rerouted in $(V,T')$ to follow the portion of $P$ from $v'$ to $v$ then the edge $e$ and then the portion of $P$ from $w$ to $w'$
	- $(V,T')$ is acyclic because the only cycle in $(V,T'\cup\{e'\})$ is the one composed of $e$ and the path $P$ and this is not in $(V,T')$ because we deleted $e'$
	- $e'$ has one end in $S$ and the other in $V-S$ but $e$ is the cheapest edge so $c_e<c_{e'}$ so $T'$ is less than $T$
- Kruskal's Algorithm produces a minimum spanning tree of G
	- Consider any edge $e=(v,w)$ added by Kruskal's algorithm and let $S$ be the set of all nodes to which $v$ has a path at the moment just before $e$ is added
	- $v\in S, w\notin S$  because adding $e$ does not create a cycle
	- No edge from $S$ to $V-S$ has been encountered yet because any edge could be added without creating a cycle and have been added by Kruskal's algorithm
	- $e$ is the cheapest edge with one edge in $S$ and the other in $V-S$ so it belongs to every MST
	- Show the output $(V,T)$ of Kruskal's Algorithm is a spanning tree of $G$
	- $(V,T)$ contains no cycles and if $(V,T)$ is not connected there would exists a nonempty subset of nodes $S$ such that there is no edge from $S$ to $V-S$
	- Contradiction because $G$ is connected and there is at least one edge between $S$ and $V-S$ and the algorithm adds the first of these that it encounters
- Prim's Algorithm produces a minimum spanning tree of $G$
	- It only adds edges belonging to every minimum spanning tree
	- In each iteration of the algorithm there is a set $S\subseteq V$ which a partial spanning tree has been constructed and a node $v$ and edge $e$ are added that minimizes the cost
	- By definition $e$ is the cheapest edge with one end in $S$ and the other end in $V-S$; by Cut Property it is in every minimum spanning tree
- Cycle Theory: Assume that all edge costs are distinct. Let $C$ be any cycle in $G$ and let edge $e=(v,w)$ be the most expensive edge in $C$. Then $e$ does not belong to any minimum spanning tree of $G$
	- Let $T$ be a spanning tree that contains $e$; show $T$ does not have the minimum cost by swapping $e$ for a cheaper edge so that we still have a spanning tree
	- Delete $e$ from $T$, partitioning the nodes into two components $S$ with node $v$ and $V-S$ with node $w$. 
	- The edge we use instead of $e$ should have one end in $S$ and the other in $V-S$ to stitch the tree together
	- We find an edge by following the cycle $C$. The edges of $C$ form a path $P$ with one end at $v$ and the other at $w$. Following $P$ from $v\rightarrow w$ we begin in $S$ and end in $V-S$ so there is some edge $e'$ on $P$ that crosses from $S$ to $V-S$
	- Consider the set of edges $T'=T-\{e\}\cup\{e'\}$. The graph $(V,T')$ is connected and has no cycles so $T'$ is a spanning tree of $G$
	- $e$ is the most expensive edge on $C$ and $e'$ belongs to $C$ so $e'<e$ so $T'<T$
- The Reverse Delete Algorithm produces a minimum spanning tree of $G$
	- Consider an edge $e=(v,w)$ removed by Reverse-Delete
	- It lies on $C$ and the first edge encountered is in decreasing order of edge costs so it must be the most expensive edge on $C$. Therefore $e$ does not belong to any MST
	- Goal: The output $(V,T)$ of Reverse Delete is a spanning tree of $G$
		- $(V,T)$ is connected because the algorithm never removes an edge when this will disconnect the graph
		- Suppose $(V,T)$ contains a cycle $C$. Considering the most expensive edge $e$ on $C$ which would have been the first one encountered by the algorithm. This edge should have been removed which would not disconnected the graph, contradicting the behavior
- Any algorithm that builds a spanning tree by repeating including edges by Cut Property and deleting edges by Cycle Property will end up with a MST
- Eliminate assumption that all edge costs are distinct
	- Take the instance and perturb all edge costs by different small numbers to become distinct
	- Any two costs that differed originally have the same relative order
	- Any MST for the new instance must have also been a MST for the original
### Implementation
- Kruskal's and Prim's Algorithm can be implemented in $O(mlogn)$ time
- We need to decide which node $v$ to add next to the growing set $S$ by maintaining the attachment costs for each node $v\in V-S$
- Keep the nodes in a priority queue with these attachment costs $a(v)$ as the keys 
- Select node with $ExtractMin$ and update attachment costs with $ChangeKey$
- There are $n-1$ iterations to perform $ExtractMin$ and $ChangeKey$ at most once for each edge
- Using a priority queue, Prim's Algorithm can be implemented on a graph with $n$ nodes and $m$ edges to run in $O(m)$ time plus the time for $n\text{ ExtractMin}$ and $m\text{ ChangeKey}$ operations
- If we use a heap based priority queue we implement $ExtractMin$ and $ChangeKey$ in $O(logn)$

