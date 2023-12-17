### Efficient Certifications
- A solves the problem X if for all strings s we have $A(s)=$yes if and only if $s\in X$
- B is an efficient certifier for a problem X if
	- B is a polynomial time algorithm that takes two input arguments s and t
	- There is a polynomial function p so that for every string s we have $s\in X$ if and only if there exists a string t such that $|t|\leq p(|s|)$ and $B(s,t)=yes$
- NP is the set of all problems for which there exists an efficient certifier
	- $P\subseteq NP$ where P is the set of all problems X for which there exists an algorithm A with polynomial running time that solves X
- Ask is there a problem in NP that does not belong to P; Does P=NP
### NP Complete Questions
- NP Complete Properties: $X\in NP$ and for all $Y\in NP,Y\leq_p X$
- Suppose X is an NP-complete problem, then X is solvable in polynomial time if and only if P=NP
	- If P=NP then X can be solved in polynomial time since it belongs to NP
	- Suppose X can be solved in polynomial time if Y is any other problem in NP then $Y\leq_p X$ and Y can be solved in polynomial time so $NP\subseteq P$
- If there is any problem in NP that cannot be solved in polynomial time than no NP complete problem can be solved in polynomial time
- Circuit Satisfiability is NP complete
- If Y is an NP complete problem and X is a problem in NP with $Y\leq_p X$ then X is NP complete
	- $X\in NP$ so let Z be any problem in NP $Z\leq_p Y$ by NP completeness of Y and $Y\leq_p X$ by assumption so $Z\leq_p X$
- 3-SAT is NP complete
	- Proof
- Independent set, set packing, vertex cover and set cover is NP complete
### General Strategy for Proving New Problems NP Complete
- Given a new problem X, prove it is NP Complete
	- Prove $X\in NP$
		- What is the certifier for a yes input to X
		- What does the certifier algorithm do to check the certifier indeed shows the answer for the input is yes
	- Choose a problem Y that is known to be NP complete
	- Prove $Y\leq_p X$ or Consider an arbitrary instance $s_y$ of problem Y and show how to construct in polynomial time an instance $s_x$ of $X$ that satisfy the properties
		- If $s_y$ is an yes instance of $Y$ then $s_x$ is a yes instance of $X$
		- If $s_x$ is an yes instance of $X$ then $s_y$ is a yes instance of $Y$
		- This shows $s_y=s_x$
