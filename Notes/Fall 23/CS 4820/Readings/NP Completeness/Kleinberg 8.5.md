- Traveling Salesman: Given a set of distances on n cities and a bound D is there a tour of length of at most D?
- Hamiltonian: Given a directed graph G does it contain a Hamiltonian cycle?
### Hamiltonian Cycle is NP Complete
- Prove Hamiltonian Cycle is in NP
	- Given a directed graph G, a certificate that there is a solution is the ordered list of vertices on a Hamiltonian cycle
	- We can check in polynomial time that this list of vertices does contain each vertex exactly once and each consecutive pair in the ordering is joined by an edge
- Show $3SAT\leq_p$ Hamiltonian
	- Consider an instance of 3SAT with variables x and clauses C
		- Describe a graph with $2^n$ different Hamiltonian cycles that correspond to the $2^n$ truth assignments to the variables; then we add nodes to model the clause constraints
	- 3SAT is satisfiable if and only if G has a Hamiltonian cycle
		- Suppose there is a satisfying assignment for the 3SAT instance (proof)
		- Suppose there is a Hamiltonian cycle in G
### Proving Traveling Salesman is NP Complete
- Traveling Salesman is NP complete
	- The certificate is a permutation of the cities and a certifier checks the length of the tour is at most the given bound
- Hamiltonian $\leq_p$ TS
- Given a directed graph G we define the instance of TS
- G has a Hamiltonian cycle if and only if there is tour of length at most n in our TS instance
	- Both Cases
### Proving Hamiltonian is NP Complete
- Hamiltonian is in NP
	- A certificate can be a path in G and a certifier can check it is in a path and contains each node exactly once
- To show Hamiltonian is NP Complete
	- Use a reduction from 3SAT
	- Prove Hamiltonian Cycle $\leq_p$ Hamiltonian Path
- G' contains a Hamiltonian path if and only if G contains a Hamiltonian cycle
To prove that the Hamiltonian Cycle problem is NP-complete, we need to demonstrate two things: first, that the Hamiltonian Cycle problem is in NP, and second, that any problem in NP can be reduced to the Hamiltonian Cycle problem in polynomial time. Let's break down the proof:

### Step 1: Hamiltonian Cycle is in NP
- A problem is in NP if a solution to the problem can be verified in polynomial time. 
- For the Hamiltonian Cycle problem, given a graph and a proposed cycle, we can easily check in polynomial time whether the cycle visits every vertex exactly once (hence forming a Hamiltonian Cycle).
- The verification involves checking that each vertex appears once in the cycle and that adjacent vertices in the cycle are connected by an edge in the graph.

### Step 2: Reduction from an NP-Complete Problem to Hamiltonian Cycle
- To show that the Hamiltonian Cycle problem is NP-complete, we typically reduce a known NP-complete problem to it. One common approach is to reduce from the NP-complete problem 3-SAT (3-satisfiability) to the Hamiltonian Cycle.
- **Reduction from 3-SAT to Hamiltonian Cycle**:
  1. **Start with a 3-SAT Instance**: Given a 3-SAT formula with variables and clauses.
  2. **Construct a Graph**: Build a graph where each clause in the 3-SAT formula is represented by a part of the graph (often called a 'gadget'). These gadgets are interconnected in such a way that a Hamiltonian Cycle can exist in the entire graph if and only if the 3-SAT formula is satisfiable.
  3. **Design of Gadget**: Each gadget should be designed to represent a clause in a way that the cycle passes through it if and only if the clause is satisfied. Typically, the construction ensures that selecting a path through each gadget corresponds to satisfying the literals of the clause.
  4. **Interconnections**: The gadgets are connected in a way that forces the cycle to make a consistent truth value choice for each variable across all clauses.
  5. **Ensuring Polynomial Time**: The construction of the graph is done in such a way that the size of the graph is polynomial in the size of the 3-SAT instance.

### Conclusion
- If the 3-SAT formula is satisfiable, then there exists a Hamiltonian Cycle in the constructed graph. Conversely, if there is a Hamiltonian Cycle in this graph, the 3-SAT formula is satisfiable. 
- Since 3-SAT is NP-complete, and we have shown a polynomial-time reduction from 3-SAT to the Hamiltonian Cycle problem, this implies the Hamiltonian Cycle problem is also NP-complete.

This proof demonstrates the intricacy of polynomial-time reductions and how they are used to establish the complexity class of problems in computational complexity theory.