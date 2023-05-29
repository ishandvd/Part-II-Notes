


# Section 2 - Alignment
##### Sequence Alignment

We use a **scoring matrix** that contains values proportional to the probability that amino acid $i$ mutates into amino acid $j$ for all pairs of amino acids.

Constructed by assembling a large and diverse sample of verified pairwise alignments (or multiple sequence alignments) of amino acids. They should reflect the true probabilities of mutations occurring through a period of evolution.

##### Global Alignment Problem
##### Local Alignment Problem
##### Middle Edge Problem

##### Longest Common Subsequence
##### Edit Graph
##### Needleman-Wunsch Algorithm

**Input:** A cost function matrix $s$ (the [[All Topics#Sequence Alignment|scoring matrix]]), a gap cost $d$, and two sequences $a,b$.
**Output:** A match describing the insertions, deletions, substitutions, and matches between the two sequences.

**Runtime:** **Time:** $\mathcal{O}(mn)$ for sequences of length $m$ and $n$. **Space:** same as time.

Typically used for [[All Topics#Global Alignment Problem|global alignment]], it uses a matrix $s_{a,b}$ that describes the ___ and a value $d$ that describes the distance. Needleman-Wunsch is a **dynamic programming** method.

The linear gap penalty $c_L(\mathrm{gap~length}) = \mathrm{gap~length} \cdot d$ assigns a penalty that is linear to the insert/deletion gap length. We have $G < 0$.

The **affine gap penalty** has a fixed gap cost for opening a gap follow by a linear cost for extending the gap: $$
c_A(\mathrm{gap~length}) = d + (\mathrm{gap~length}-1) \cdot E
$$
Gaps usually occur in bunches so we use a convex gap penalty function $\gamma(n + 1) - \gamma(n) \leq \gamma(n) - \gamma(n - 1)$ for all $n$. ![[Pasted image 20230528220913.png]]

Blast.ncbi.nlm.gov - Can be used for Needleman-Wunsch.

The solution is the optimal path through a 2-d grid that optimises the total score when going through that path.

We start with a grid $F$ of size $|a| + 1$ rows and $|b| + 1$ columns, with the first column set to $F_{i, 0} = i \times d$ and the first row set to $F_{0, j} = j \times d$.

We update the grid row by row from left to right with:

$$
\begin{align}
F_{i,j} = max\left\{
\begin{array}{ll}
F_{i-1, j-1} + S_{a[i], b[j]}   & \mathrm{If~match/mismatch} \\
F_{i-1,j}   + d  & \mathrm{gap~in~b}\\
F_{i, j-1} + d  & \mathrm{gap~in~a}
\end{array}
\right.
\end{align}
$$
The only way to **add** a reward is if we go diagonally (i.e. we accept a match/mismatch); this also assumes that $S_{a[i], b[j]} > 0$.

We **chug along** to the right if there is gap in $a$ (the vertical sequence on the left) and **chug along** downwards if there is a gap in $b$ (the horizontal sequence at the top).

![[Pasted image 20230528200924.png]]

It might be helpful to keep track of a **traceback matrix** that keeps track of the direction we came from at each point.


##### Smith-Waterman Algorithm

Input:** A cost function matrix $s$, a gap cost $d$, and two sequences $a,b$.
**Output:** A match describing the insertions, deletions, substitutions, and matches between the two sequences.

**Runtime:** $\mathcal{O}(mn)$ for sequences of length $m$ and $n$. **Space**: Same as time.

Used for [[All Topics#Local Alignment Problem|local alignment]]. The stretches of the sequences with the highest density of matches. Ignores badly aligned regions.
- Aligns regions having highest similarities between 2 sequences
- More suitable for **partially similar**, **different length** and **conserved regions** containing sequences. I.e. if you don't want to introduce too many insertions/deletions.
- Align substring of target sequence (a) of substrings of query sequence (b).
- Suitable for **divergent sequences**.
- Most general local alignment algorithm is **Smith-Waterman**.

Steps:
- Initialization of $F$
- Matrix filling ($F$)
- Traceback


Identical to [[All Topics#Needleman-Wunsch Algorithm|Needleman-Wunsch]] except now negative values become zero. i.e. our dynamic programming function is:

$$
\begin{align}
F_{i,j} = max\left\{
\begin{array}{ll}
0  & \mathrm{No~traceback~in~this~case}\\
F_{i-1, j-1} + S_{a[i], b[j]}   & \mathrm{If~match/mismatch} \\
F_{i-1,j}   + d  & \mathrm{gap~in~b}\\
F_{i, j-1} + d  & \mathrm{gap~in~a}
\end{array}
\right.
\end{align}
$$

We initialise using: $F_{0,0} = F_{0,j} = F_{i,0} = 0$.
![[Pasted image 20230528214119.png]]
**Termination:**

If we want the **best** local alignment we use: $F_{\mathrm{OPT}} = \mathrm{max}_{i,j}~F_{i,j}$. This will hopefully give us one of the values at the end of the blue trails in the diagram above. We then need to traceback to find the whole local alignment match.

If we want **all** local alignments with score $> t$, we use:
$$
\mathrm{For~all~i,j~find~}F_{i,j} > t~\mathrm{and~trace~back}
$$

##### Hirshberg Algorithm
##### Banded Dynamic Programming

**Runtime:** Time, Space: $\mathcal{O}(N \times k(N)) \ll \mathcal{O}(N^2)$, where $N, M$ are the lengths of the input and $N > M$.

Assuming we know that a and b are similar, the optimal alignment of a and b has few gaps. The path of the alignment will be close to diagonal.

![[Pasted image 20230528220012.png]]
**Initialisation**:
$$
F_{i,0}~\mathrm{and}~F_{0,j}~\mathrm{undefined~for}~i,j > k
$$
**Iteration**:

For i = 1...M:
	For j = $\mathrm{max}(1, i - k) \dots \mathrm{min}(N, i + k)$: # Keeps us in the band as above
		![[Pasted image 20230528220629.png]]

**Termination:**
Same as Needleman-Wunsch.
Easy to extend to the affine gap case.

##### Divide and Conquer Approach to Sequence Alignment
##### Linear Space Alignment Algorithm
##### Four-Russian Algorithm
##### Nussinov Folding Algorithm

# Section 3 - Building Trees

##### Distance-Based Phylogeny Problem

![[Pasted image 20230527081441.png]]

**Theorem:** There is a unique simple tree fitting an additive matrix.
**Simple Tree:** Tree with no nodes of degree 2 (as in diagram above). If we had a node of degree two, we would simply join its two neighbours with the sum of the distances to those neighbours, and get rid of our original node.

**Additive Matrix:** Distance matrix such that there exists an unrooted tree fitting it.

**Distance Matrix:** Matrix of species containing $D_{i,j} = \mathrm{number~of~differing~symbols~between~i-th~and~j-th~species}$.

**Leaf**: Present day species (degree = 1).
**Internal nodes:** (Degree $\geq$ 1) ancestral species.
**One node** designated as root (most recent common ancestor).

Construct an evolutionary tree from a distance matrix.

**Input:** a distance matrix.
**Output:** The **simple tree** fitting this distance matrix (**if** the matrix is additive).



##### Least-Squares Distance-Based Phylogeny Problem

Given a distance matrix, find the tree that minimizes the sum of squared errors. A tree can be constructed to have a least-squares error of 0, but this is only possible for additive matrices.

**Input:** An $n \times n$ distance matrix D.
**Output:** A weighted tree T with n leaves minimising **Discrepancy(T,D)** over all weighted trees with $n$ leaves.

This problem is NP-complete.

$$
\mathrm{Discrepancy(T,D)}= \sum_{1 \leq i< j \leq n}(d_{i,j}(T) - D_{i,j})^2
$$
![[Pasted image 20230527080703.png]]

##### Small Parsimony Problem




**Input:** An unrooted tree and a cost function $\delta_{i,j}$ that tells you the cost of swapping from one symbol to another.
**Output**: A labelling of the tree that minimises the parimony score. That is, it outputs the **most parsimonious** tree.

##### Large Parsimony Problem

##### Limb Length Theorem

$\mathrm{LimbLength(chimp)} = \mathrm{min}((D_{\mathrm{chimp},k} + D_{\mathrm{chimp},j} - D_{j,k}) / 2)$

![[Pasted image 20230527081135.png]]


##### Additive Phylogeny

**BTW phylogeny just means evolutionary.**

**Input:** A distance matrix (must be additive).
**Output:** A tree that perfectly matches the distance matrix.

1. Pick an arbitrary leaf j.
2. Compute limb length using [[All Topics#Limb Length Theorem|limb length equation]].
3. Subtract this LimbLength value from each row and column to produce a matrix $D^{\mathrm{bald}}$ in which j is a bald limb (length 0).
4. Remove the j-th row and column of the matrix to form $D^{\mathrm{trim}}$.
5. Construct Tree($D^{\mathrm{trim}}$).
6. Identify the point in Tree($D^{trim}$) where leaf j should be attached.
7. Attach j by an edge of length LimbLength(j) to form Tree(D).

##### UPGMA Algorithm


**Input:** Distance matrix of clusters of size 1.
**Output:** Ultra-metric Tree

**Ultrametric tree:** **Rooted binary tree** (an unrooted binary tree with a root of degree 2 on one of its edges). **Edge weights** correspond to difference in ages on the nodes the edge connects. Distance from root to any leaf is the same (i.e. age of root).

**Produces a tree for any matrix**
**Doesn't necessarily fit an additive matrix**

**Runtime:** A trivial implementation of the algorithm to construct the UPGMA tree has $\mathcal{O}(n^3)$ time complexity, and using a heap for each cluster to keep its distances from other cluster reduces its time to $\mathcal{O}(n^2 \log n)$. Fionn Murtagh presented an $\mathcal{O}(n^2)$ time and space algorithm.

Equation 1: $$
d_{kl} = \frac{1}{|C_k||C_l|} \sum_{p \in C_k, q \in C_l} d_{pq}
$$

1. Group together the two clusters with the smallest distance.
2. Replace the two clusters with a larger cluster $a = C_1 \cup  C_2$.
3. Find the distance from $a$ to all other clusters.
4. Set the "age" of $a = d_{c_1,C_2} / 2$ (half the distance from $C_1$ to $C_2$).
5. Redo step 1 until you have a $2 \times2$ matrix, at which point you can join the last two clusters.


##### Neighbour-Joining Algorithm

Greedy algorithm (like UPGMA). Can find an additive tree in polynomial time.



##### Tree Validation: Bootstrap Algorithm
##### Progressive Alignment Algorithm

# Section 4 - Clustering

##### Clustering Problem
##### K-Center Clustering Problem
##### Coin Flipping Problem


##### Lloyd Algorithm
##### Soft vs Hard Clustering
##### K-means Clustering Algorithm
##### Expectation Maximisation Algorithm
##### Hierarchical Clustering
##### Markov Clustering Algorithm
##### Louvain Clustering
##### Leiden Clustering

# Section 5 - Genome Sequencing

##### K-Mer Composition Probem
##### String Reconstruction from Read-Pairs Problem
##### Eulerian Path Problem (and Hamiltonian)
##### Eulerian Cycle Problem (and Hamiltonian)

##### Paired De Bruijn Graphs

# Section 6 - Genome Assembly

##### Read Mapping
##### Single Pattern Matching Problem
##### Multiple Pattern Matching Problem

##### Prefix Trie
##### Suffix Trie and Pattern Matching
##### Run Length encoding
##### Suffix Array
##### Burrows-Wheeler Transform (BWT)

# Section 7 - Parts Identification
##### Identifying protein parts


##### Viterbi
##### Forward
##### Backward

# Section 8 - DNA Computing

##### Hamiltonian Problem
##### Random Access in Large-Scale DNA Data Storage

#### Adleman's Computation Approach



# Section 9 - Simulations


#### Doob-Gillespie Algorithm
