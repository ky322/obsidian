### Packing Problems
- Given a collection of objects, choose at least k but with a set of conflicts
	- Independent set: Given a graph G and a number k does G contain an independent set of size at least k?
	- Set Packing: Given a set U of n elements a collection S of subsets of U and a number k does there exist a collection of at least k of these sets with the property that no two of them intersect?
### Covering Problem
- Given a collection of objects choose a subset that collectively achieves a goal but only choose k objects
	- Vertex Cover: Given a graph G and a number k does G contain a vertex cover of size at most k
	- Set Cover: Given a set U of n elements a collection S of subsets of U and a number k does there exist a collection of at most k of these sets whose union is equal to all of U?
### Partitioning Problems
- Divide up a collection of objects into subsets so that each object appears in exactly one of the subsets
	- 3Dimensional Matching: Given disjoint sets X,Y,Z each of size n and given a set $T\subseteq X\times Y\times Z$ does there exist a set of n triples in T so that each element of $X\cup Y\cup Z$ is contained in exactly one of these triplets
### Sequencing Problem
- Searching over the set of all permutations of a collection of objects and searching over a subset of a collection of objects
- We have to order n objects but in a certain order
	- Hamiltonian Cycle and Path
	- Traveling Salesman
### Numerical Problem
- Subset Sum: Given natural numbers and a target number W is there a subset of numbers that add up to W?
- Try reducing if a problem has a weighted objects and the goal is to select objects for a total weight
### Constraint Satisfaction Problems
- 3SAT: Given a set of clauses each of length 3 over a set of variables X does there exist a satisfying truth assignment?
- Use it like a search over assignments where all clauses have to be satisfied
- A search over ways to choose a single term from each clause where we cannot choose conflicting terms from different clauses
