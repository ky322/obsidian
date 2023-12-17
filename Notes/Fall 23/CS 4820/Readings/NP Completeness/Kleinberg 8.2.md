- SAT: Given a set of clauses over a set of variables X does there exist a satisfying truth statement
- 3-SAT: Given a set of clauses each of length 3 over a set of variables X does there exist a satisfying truth statement
- $3SAT\leq_p$ Independent Set
- $\leq_p$ is a transitive relation
- 
To prove that 3-SAT is polynomial-time reducible to Independent Set we need to show how any instance of the 3-SAT problem can be transformed into an instance of the Independent Set problem in polynomial time, such that a solution to the Independent Set instance gives us a solution to the original 3-SAT instance. Here’s a step-by-step breakdown of the reduction process:

### 3-SAT Problem

- **Given**: A 3-SAT problem is a Boolean satisfiability problem where we are given a boolean formula in conjunctive normal form (CNF) where each clause has exactly three literals.
- **Goal**: Determine if there exists a truth assignment to the variables that satisfies the entire formula.

### Independent Set Problem

- **Given**: A graph G and a number k.
- **Goal**: Determine if there exists a set of k vertices in G, none of which are adjacent, i.e., an independent set of size k.

### Reduction from 3-SAT to Independent Set

1. **Constructing the Graph from 3-SAT Instance**:
    
    - For each clause in the 3-SAT formula, create a triangle (a completely connected subgraph of 3 nodes) in the graph. Each vertex of this triangle represents one literal of the clause.
    - Connect vertices across triangles if they represent conflicting literals (a literal and its negation).
2. **Setting the Size of the Independent Set**:
    
    - Set the size of the independent set, k, to be the number of clauses in the 3-SAT formula.
3. **Implications**:
    
    - If the original 3-SAT formula is satisfiable, then each clause has at least one true literal. In the graph, this means for each triangle (representing a clause), there is at least one vertex that can be part of the independent set (since that literal is true and doesn’t conflict with others).
    - Conversely, if there is an independent set of size k in the constructed graph, it means we can pick one vertex from each triangle without picking conflicting literals. This corresponds to a satisfying assignment for the 3-SAT formula (each picked vertex/literal can be set to true).
4. **Polynomial Time**:
    
    - The construction of the graph from the 3-SAT instance is done in polynomial time, as it involves creating a fixed number of vertices and edges for each clause in the formula.

### Conclusion

This reduction shows that solving the Independent Set problem on the constructed graph would also solve the 3-SAT problem for the original formula. Since we know that 3-SAT is NP-Complete, and we've demonstrated a polynomial-time reduction to Independent Set, this implies that Independent Set is at least as hard as 3-SAT, reinforcing the NP-Hardness of the Independent Set problem.