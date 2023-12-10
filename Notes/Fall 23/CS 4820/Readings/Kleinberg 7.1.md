- A bipartite graph $G=(V,E)$ is an undirected graph whose node set can be partition as $V=X\cup Y$ where every edge $e\in E$  has one end in $X$ and one in $Y$
- For a graph the edges are a pair of nodes and a matching in graph G is a set of edges $M\subseteq E$ where each node appears in at most one edge of $M$
- A set of edges $M$ is a perfect matching if every node appears in exactly one edge of $M$
	- G has a perfect matching if and only if $|X|=|Y|$ and has a matching size of $|X|$
### Flow Networks
- A flow network is a directed graph $G=(V,E)$ 
	- Each edge $e$ has a capacity $c_e$
	- There is a single source node $s\in V$ and a single sink node $t\in V$
	- Assume no edge enters the source and no edge leaves the sink and assume there is at least one edge incident to each node and all capacities are integers
- An s-t flow is a function f that maps each edge e to a nonnegative real number $f:E\rightarrow\mathbb{R}^+$ 
	- $f(e)$: the amount of flow carried by edge $e$
	- Capacity conditions: For each $e\in E$ $0\leq f(e)\leq c_e$
	- Conservation Conditions: For each node $v$ other than $s$ and $t$ $\sum_{\text{e into v}}f(e) =\sum_{\text{e out of v}}f(e)$
	- A flow on an edge cannot exceed the capacity of the edge and for every node other than the source and the sink the amount of flow entering must equal the flow leaving
	- $v(f)$: the value of a flow $f$; the amount of flow generated at the source $v(f)=\sum_{\text{e out of s}}f(e)$
### Maximum Flow Problem
- Given a flow network find a flow of maximum possible value
- The maximum flow value equals the minimum cut
- Residual Graph $G_f$: Given a flow network $G$ and a flow $f$ on $G$, the node set of $G_f$ is the same of $G$
	- Forward Edges: For each edge $e=(u,v)$ of $G$ where $f(e)<c_e$ there are $c_e-f(e)$ leftover units of capacity which we can push flow forward so we include e in $G_f$ with capacity $c_e-f(e)$
	- Backward Edges: For each edge e of G where $f(e)>0$ there are $f(e)$ units of flow we can undo so we include $e'=(v,u)$ in $G_f$ with capacity $f(e)$
- Let $P$ be a simple s-t path in $G_f$; P does not visit any node more than once
- `bottleneck(P,f)` is the minimum residual capacity of any edge on P
- `augment(f,P)` yields a new flow $f'$ in $G$
```
Let b=bottleneck(P,f)
For each edge (u,v) in P
	If e=(u,v) is a forward edge then
		Increase f(e) in G by b
	Else let e=(v,u)
		Decrease f(e) in G by b
Return f
```
#### f' is a flow in G
- Verify capacity and conservation conditions
- Only check the capacity condition on these edges since f' differs from f only on the edges of P
	- If e is a forward edge we avoid increasing flow on e above $c_e$ and if e is a backwards edge we avoid decreasing flow on e below 0
- Conservation condition: Check condition at each internal node that lies on P
	- We verify that for node v the change in amount of flow entering v is the same as the change in flow exiting v
	- If f satisfied the conservation condition at v so much f'
### Ford Fulkerson Algorithm
```
f(e) = 0 for all e in G
While there is an s-t path in Gf
	Let P be a simple s-t path in Gf
	f'=augment(f,P)
	Update f to be f'
	Update Gf to be gf'
Return f
```
#### Termination and Running Time
- At every intermediate stage of the Ford Fulkerson Algorithm the flow values and the residual capacities in $G_f$ are integers
	- Suppose it is true after j iterations then all residual capacities in $G_f$ are integers and the value `bottleneck(P,f)` for the augmenting path found in iteration j+1 be an integer
	- Flow f' will have integer values and so the will the capacities of the new residual graph
- A measure of progress that implies termination
- Let f be a flow in G and let P be a simple s-t path in Gf. Then $v(f')=v(f)+\text{bottleneck}(P,f)$ and since $\text{bottleneck}(P,f)>0$, $v(f')>v(f)$
	- The first edge e of P must be an edge out of s in the residual graph $G_f$ and since the path is simple it does not visit s again. G has no edges entering s so e must be a forward edge.
	- We increase flow on any other edge incident to s so the value f' does not exceed the value of f by $\text{bottleneck}(P,f)$
- We need to bound the maximum possible flow value
- Suppose that all capacities in the flow network G are integers then the FF algorithm terminates in at most C iterations of the while loop
	- No flow in G can have value greater than C due to the capacity condition on the edges leaving s
	- The value of the flow maintained by the FF increases in each iteration by the measure of progress by the integer rule it increases by at least 1 in each iteration
	- It starts with 0 and cannot exceed C so the while loop in the FF algorithm can run for at most C iterations
- Let n be the number of nodes in G and m be the number of edges in G. 
	- All nodes have one incident edge so $m\geq n/2$ giving $O(m)$ time
- Suppose that all the capacities in the flow network G are integers, then the FF algorithm can be implemented to run in $O(mC)$ time
	- The algorithm terminates in at most C iterations of the while loop so we consider the amount of work in one iteration when the current flow is f
	- The residual graph $G_f$ has at most 2m edges because each edge of G gives at most two edges in the residual graph
	- We maintain $G_f$ using an adjacency list representation; we have two linked lists for each node $v$ one for edges entering v and one for edges leaving s
	- To find an s-t path in $G_f$ we use BFS or DFS which is $O(m+n)$ time
	- `augment(f,P)` takes $O(n)$ because the path P has at most $n-1$ edges
	- Given the new flow $f'$ we can build the new residual graph in $O(m)$ time
	- For each edge e of G we construct the forward and backward edges in $G_f'$