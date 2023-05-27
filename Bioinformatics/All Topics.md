


# Section 2 - Alignment
##### Sequence Alignment
##### Global Alignment Problem
##### Local Alignment Problem
##### Middle Edge Problem

##### Longest Common Subsequence
##### Edit Graph
##### Needleman-Wunsch Algorithm
##### Smith-Waterman Algorithm
##### Hirshberg Algorithm
##### Banded Dynamic Programming
##### Divide and Conquer Approach to Sequence Alignment
##### Linear Space Alignment Algorithm
##### Four-Russian Algorithm
##### Nussinov Folding Algorithm

# Section 3 - Building Trees

##### Limb Length Problem
##### Distance-Based Phylogeny Problem
##### Least-Squares Distance-Based Phylogeny Problem

Given a distance matrix, find the tree that minimizes the sum of squared errors.

**Input:** An $n \times n$ distance matrix D.
**Output:** A weighted tree T with n leaves minimising **Discrepancy(T,D)** over all weighted trees with $n$ leaves.

This problem is NP-complete.

##### Small Parsimony
##### Large Parsimony Problem

##### Limb Length Theorem
##### Additive Phylogeny


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
