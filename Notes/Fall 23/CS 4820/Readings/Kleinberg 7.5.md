### Bipartite Matching Problem
- Recall a bipartite graph [[Kleinberg 7.1]]
- Find a matching in G of largest size 
- Begin with the graph G and construct a flow network $G'$
	- Direct all edges in $G$ from $X$ to $Y$
	- Then add node s and an edge $(s,x)$ from s to each node in $X$
	- Add node t and an edge $(y,t)$ from each node in $Y$ to t
	- Give each edge in $G'$ a capacity of 1
- We then compute a maximum s-t flow in this network $G'$ and the value of this maximum is equal to the maximum matching in $G$
### Analysis
- Show integer valued flows in $G'$ encode matchings in G in a transparent fashion
- Suppose there is a matching in G consisting of k edges
	- Consider the flow f that sends one unit along each path of the form $s,x_i, y_i,t,f(e)=1$ for each edge on one of these paths
	- We can verify the capacity and the conservation conditions are met and f is an s-t flow of value k
- Suppose there is a flow f' in G' of value k
	- By the integrality theorem for max flows there is an integer valued flow f of value k
	- Since all capacities are 1 f(e) is equal to 0 or 1 for each edge e
- Now Consider the set $M'$ of edges of the form $(x,y)$ on which the flow value is 1
	- $M'$ contains k edges: Consider the cut $(A,B)$ in G' with $A=\{s\}\cup X$. The value of the flow is the total flow leaving A minus the flow entering A
		- The first is the cardinality of M' because these are the edges leaving A that carry flow and each carries one unit of flow
		- The second term is 0 because there is no edges entering A so M' contains k edges
	- Each node in X is the tail of at most one edge in M'; Each node in Y is the head of at most one edge in M;
		- Suppose $x\in X$ was the tail of at least two edges in M'. Our flow is integer valued so at least two units of flow leave from x. By conservation of flow at least two units of flow would come into x but this is not possible
- The size of the maximum matching in G is equal to the value of the maximum flow in G' and the edges in such a matching in G are the edges that carry flow from X and Y to G'
### Running Time
- Let $n=|X|=|Y|$ and m = number of edges in G
- Assume there is at least one edge incident to each node and $m\geq n/2$
- Time to compute a maximum matching is dominated by time to compute an integer valued maximum flow in $G'$
- The FF finds a maximum matching in a bipartite graph
### Bipartite Graphs With No Perfect Matching
- If the algorithm concludes that there is no perfect matching then it could produce a certificate
- We decide if graph G has a perfect matching by checking if the maximum flow in related graph $G'$ has value at least $n$
- By the Max Flow cut theorem there will be an s-t cut of capacity less than n if the maximum flow value in G' has value less than n
	- A cut with capacity less than n has that certificate
### Hall's Theorem
- Assume that the bipartite graph $G=(V,E)$ has two sides X and Y such that $|X|=|Y|$. Then G either has a perfect matching or there is a subset $A\subseteq X$ such that $|\Gamma(A)|<|A|$
- A perfect matching or an appropriate subset $A$ can be found in $O(mn)$ time
	- Assume $|X|=|Y|=n$ the graph G has a maximum matching if and only if the value of maximum flow in G' is n
	- If the max flow is less than n then there is a subset A such that $|\Gamma(A)|<|A|$
	- By max flow min cut theorem, if the maximum flow is less than n then there is a cut $(A',B')$ with capacity less than n in G'
	- One can modify the cut minimum $(A',B')$ so $\Gamma(A)\subseteq A'$ where $A=X\cap A'$
	- Consider a node $y\in\Gamma(A)$ that belongs in $B'$. By moving y from $B'$ to $A'$ we do not increase capacity of the cut
	- The capacity of this minimum cut $(A',B')$ that has $\Gamma(A)\subseteq A'$ because all neighbors of A belong to A' so only edges out of A' are edges that leave the source s or enter the sink t