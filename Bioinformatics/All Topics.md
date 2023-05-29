


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

**Uses a multiple alignment to determine the most likely ancestral tree**.

**Parsimony Score**: Sum of the Hamming distances along each edge of the tree.



**Input:** An unrooted binary tree and a cost function $\delta_{i,j}$ that tells you the cost of swapping from one symbol to another.
**Output**: A labelling of the tree that minimises the parsimony score. That is, it outputs the **most parsimonious** tree.

##### Large Parsimony Problem

Large Parsimony Problem: Given a set of strings, find a tree (with leaves labeled by all these strings) having minimum parsimony score. 
- **Input**: A collection of strings of equal length.
- **Output**: A rooted binary tree T that minimises the parsimony score among all possible rooted binary trees with leaves labeled by these strings.

**This problem is NP complete.**


##### Parsimony Algorithm

Solves the [[All Topics#Small Parsimony Problem|Small Parsimony]] problem.

**Runtime:** : if we want to calculate the overall length (cost) of a tree with m species, n characters, and k states, the Parsimony algorithm is of complexity $\mathcal{O}(mnk^2)$.

Treating the columns of the multiple alignment as independent of each other; solve the small parsimony problem on each column of the alignment separately. Can work with one symbol from each string at a time.

We assume $\delta_{i,j} = 0~\mathrm{if~i=j~else~1~otherwise}$


![[Pasted image 20230529194957.png]]
**Initialisation:** The leaves of the tree are hardcoded, they encode the species of whom we're trying to build a tree.

**Iteration**: Consider the left-most node in the 2nd from top row in the image above. We can calculate the score $s_k(v)$ for this node $v$ for each symbol $k \in \{A,C,G,T\}$. Let us do $k = A$. For the left child (the Daughter) we take the min of all possible symbols plus the corresponding $\delta_{i,j}$. In this case, the minimising left child symbol would be C as $0 + 1 = 1$ which is the minimum parsimony from the left subtree. Similarly, the min parsimony from the right subtree is $1 + 0 = 1$ in the case of $A$ in the right child (the Son). This gives a total of $2$. We must remember that we picked $C,A$ as the left and right children A to help with backtracking.


**Termination and backtracking:** Once we have the parsimony values of $A,C,T,G$ for the root of the tree, we choose the one with the smallest value. We then pick the left and right node symbols based on the symbols that gave us this minimal root value. We continue recursively down the tree with this.

##### Greedy Heuristic for Large Parsimony

Removing an **internal edge**, an edge connecting two internal nodes (along with the nodes) produces four subtree (W,X,Y,Z).

![[Pasted image 20230529195843.png]]

Rearranging these subtrees is called the **nearest neighbour interchange**.

![[Pasted image 20230529195938.png]]

**Nearest Neighbour Interchange Heuristic**:
1. Set current tree equal to arbitrary binary rooted tree structure.
2. Go through all internal edges and perform all possible nearest neighbour interchanges.
3. Solve Small Parsimony Problem on each tree.
4. If any tree has parsimony score improving over current optimal tree, set current tree equal to this. Otherwise, keep current tree.

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

Consider m sequences, each with n nucleotides, a phylogenetic tree is reconstructed using some tree building methods.

1. From each sequence, $n$ nucleotides (symbols) randomly chosen with replacements, giving rise to $m$ rows of $n$ columns each.. These now constitute a **new set of sequences**.
2. A tree is then reconstructed with these new sequences using the same tree building method as before.
3. Topology of this tree **compared to that of original tree**. Each interior branch of original tree that is different from new **bootstrap tree** is given a score of 0; all other interior branches given value 1.
4. This procedure of resampling the sites and tree reconstruction is **repeated several hundred times**, and percentage of times each interior branch is given value 1 is noted.
5. **This is known as the bootstrap value**. Generally, if bootstrap value for a given interior branch > 95%, then topology at that branch is considered "correct".


##### Progressive Alignment Algorithm

1. Given N sequences, align each sequence against each other.
2. Use the score of the pairwise alignments to compute a distance matrix.
3. build a guide tree (tree shows best order of progressive alignment).
4. Progressive alignment guided by tree.
5. 

# Section 4 - Clustering

**Good clustering principle:** Elements within the same cluster are closer to each other than elements in different clusters.

##### Clustering Problem

*Partition a set of expression vectors into clusters*.

**Input:** A collection of n vectors and an integer k.
**Output:** Partition of n vectors into k disjoint clusters satisfying the Good Clustering Principle.

##### K-Center Clustering Problem

$\mathrm{MaxDistance(Data,~Centers) = max_{p \in Data}(dist(d, Centers))}$

$\mathrm{MaxDistance(Data, Centers) = max_{p \in Data} (dist(p, Centers))}$

**Squared Error Distortion**
$\mathrm{Distortion(Data, Centers) = \sum_{p \in Data}min(dist(p, Centers))^2 / n}$

![[Pasted image 20230529201244.png]]

Given a set of points (Data), find k centers minimising MaxDistance(Data, Centers).

**Input:** A set of points (*expression vectors*) Data, and an integer $k$.
**Output:** A set of $k$ points Centers that minimises MaxDistance(Data, Centers) over all possible choices Centers.

##### K-Means Clustering Problem
![[Pasted image 20230529201619.png]]

For k = 1, we can just apply the **Center of Gravity Theorem:**

The center of gravity of points Data is the only point that solves the 1-Means clustering problem.

**Center of Gravity** = $\sum_{p \in Data} (p / \mathrm{num~points~in~Data})$


##### Soft vs Hard Clustering

**Hard choices:** Points are assigned either completely to one cluster or another.

**Soft choices:** Points assigned cluster "responsibilities", meaning a weight to different clusters, with the sum of the weights equal to 1.

##### Coin Flipping Problem

- Flip a loaded coin with an unknow bias $\theta$, representing the probability the coin lands on heads.
- Coin lands on heads **i out of n times**.
- For each bias, we can compute the probability of the resulting seq of flip:

**Prob of generating seq:**
$Pr(\mathrm{sequence}|\theta) = \theta^i \times (1- \theta) ^ {n - i}$.

Expression maximised at $\theta = i / n$ (the most likely bias).

##### k-Centering Clustering Heuristic
The **FarthestFirstTraversal:**
![[Pasted image 20230529201348.png]]
![[Pasted image 20230529201402.png]]
This selects Centers that minimise MaxDistance(Data, Centers), but biologists are interested in typical rather than maximum deviations, since **max deviations may represent outliers** (experimental errors).

##### Lloyd Algorithm

Select $k$ arbitrary data points as Centers and then iteratively perform the following two steps:

**Centers to Clusters:** Assign each data point to the cluster corresponding to its nearest center (ties broken arbitrarily).

**Clusters to Centers:** After assignment of data points to k clusters, compute new centers as center of gravity of each cluster.

**Termination:** When centers stop moving (**convergence of centers**).



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
