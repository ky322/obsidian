- How can we construct the optimal way to take advantage of nonuniform frequencies of the letters
- Variable Length Encoding: Encode frequent letters with shorter strings
- Prefix Codes: For a set $S$ of letters is a function $y$ that maps each letter $x\in S$ to some sequence of zeros and ones that for a distinct $x,y\in S$ the sequence $y(x)$ is not a prefix of the sequence $y(y)$
- Optimal Prefix Codes: If there are $n$ letters then $nf_x$ are equal to $x$ and $\sum_{x\in S}f_x=1$
- Encoding Length: $$\sum_{x\in S}nf_x|y(x)|$$
- Given an alphabet and a set of frequencies for the letters, we want to produce a prefixed code hat minimizes the average bits per letter

### Designing the Algorithm
- For each letter $x\in S$ we follow the path from the root to the leaf labeled $x$; each time the path goes from a node to its left we write a 0; from node to right child we write a 1 and take the resulting string of bits as the encoding of $x$
- The encoding of $S$ constructed from $T$ is a prefix code
	- In order for the encoding of $x$ to be a prefix of the encoding $y$ the path from the root to $x$ would have to be a prefix of the path from the root to $y$ or $x$ would lie on the path from the root to $y$ which is not possible if $x$ is a leaf
- Given a prefix code $y$ we can build a binary tree recursively by starting with a root; all letters $x\in S$ whose encoding starts with a $0$ will be leaves in the left subtree of the root and all letters $y\in S$ whose encoding starts with a $1$ will be leaves in the right subtree of the root and build the two subtrees recursively
- The search for the optimal prefix code is searching for a $T$ that minimizes the average number of bits per letter
- The length of the encoding of a letter $x\in S$ is the length of the path from the root to the leaf labeled $x$ which is the depth
- We are seeking the labeled tree that minimizes the weighted average of the depths of all leaves where the average is weighted by the frequencies of the letters that the label the leaves
- The binary tree corresponding to the optimal prefix code is full
	- Let $T$ denote the binary tree corresponding to the optimal prefix code and suppose it contains a node $u$ with one child $v$.
	- Convert $T$ into $T'$ by replacing node $u$ with $v$
	- Two cases: If $u$ was the root we delete $u$ and use $v$ as the root, otherwise let $w$ be the parent of $u$ in $T$ then we delete $u$ and make $v$ the child of $w$
		- This decreases the number of bits needed to encode any leaf in the subtree rooted at $u$ so the prefix code corresponding to $T'$ has a smaller average of number of bits per number than the prefix code of $T$ contradicting the optimality of $T$
- Suppose $u$ and $v$ are leaves of $T^*$ such that depth(u)< depth(v). Suppose $u$ is labeled with $y\in S$ and $z\in S$ then $f_y\geq f_z$
	- If $f_y<f_z$ then in $\sum_{x\in S}f_x\text{depth(x)}$ the multiplier of $f_y$ increases and the multiplier of $f_z$ decreases
	- The change to the sum is $depth(v)-depth(u)(f_y-f_z)$ If $f_y<f_z$ then it contradicts the optimality of the prefixed code we had before the exchange
- $w$ is a leaf of $T^*$
	- If $w$ was not a leaf then there would be some leaf $w'$ in the subtree below it but $w'$ would have a depth greater than $v$ contradicting the assumption $v$ is a leaf of maximum depth in $T*$
- $v$ and $w$ are siblings that are as deep as possible in $T^*$
- There is an optimal prefix code with $T^*$ which the two lowest frequency letters are assigned to leaves that are siblings in $T^*$
- Suppose $y^*$ and $z^*$ are the lowest frequency letters in $S$ and a meta character is the common parent whose frequency is the sum of the two letters. We replace $y^*$ and $z^*$ with the meta letter and obtain an alphabet that is one letter smaller. We recursively find a prefix code for the smaller alphabet and open up to the meta letter back into $y^*$ and $z^*$ for a prefix code for $S$

### Analyzing the Algorithm
- $ABL(T') = ABL(T)-f_w$
- The Huffman Code for a given alphabet achieves the minimum average number of bits per letter of any prefix code
	- Suppose that the tree $T$ produced by the greedy algorithm is not optimal then there is some labeled binary tree $Z$ such that $ABL(Z)<ALB(T)$ and there is a tree $Z$ where the leaves $y^*$ and $z^*$ are siblings
	- If we delete $y^*$ and $z^*$ from $Z$ and label the parent $w$ we get $Z'$ that defines a prefix code for $S'$ and we get $Z$ from $Z'$ by adding $y^*$ and $z^*$ below $w$ so $ABL(Z')=ABL(Z)-f_w$
	- We assumed $ABL(Z)<ABL(T)$ and subtracting $w'$ we get $ABL(Z')<ABL(T')$ which contradicts the optimality of $T'$ as a prefix code for $S'$

### Implementation and Running Time
- The recursive call defines a sequence of $k-1$ iterations over smaller alphabets and each iteration expect for the last identifies the two lowest frequency letters and merging them into a single letter that has the combined frequency. It can be done in a single scan so $O(k)$ and summing over $k-1$ iterations gives us $O(k^2)$ time
- Using a priority queue we make each insertion and extraction of minimum in $O(logk)$ and each iteration which performs three of these operations takes $O(logk)$. Summing over $k$ iterations we have $O(klogk)$