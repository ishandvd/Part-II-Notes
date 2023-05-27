


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
##### Small Parsimony
##### Large Parsimony Problem

##### Limb Length Theorem
##### Additive Phylogeny


##### UPGMA Algorithm

**Used to solve _ parsimony problem**

Input: Distance matrix of clusters of size 1.
Output: Ultra-metric Tree

$$
Runtime: A trivial implementation of the algorithm to construct the UPGMA tree has lat (�3)![O(n^{3})](https://wikimedia.org/api/rest_v1/media/math/render/svg/6b04f5c5cfea38f43406d9442387ad28555e2609) time complexity, and using a heap for each cluster to keep its distances from other cluster reduces its time to �(�2log⁡�)![O(n^2 \log n)](https://wikimedia.org/api/rest_v1/media/math/render/svg/fd59427b9a6250e085bf2c29b06ef211c8e791e0). Fionn Murtagh presented an �(�2)![O(n^{2})](https://wikimedia.org/api/rest_v1/media/math/render/svg/6cd9594a16cb898b8f2a2dff9227a385ec183392) time and space algorithm.

Equation 1: $$
d_{kl} = \frac{1}{|C_k||C_l|} \sum_{p \in C_k, q \in C_l} d_{pq}
$$

1. Group together the two clusters with the smallest distance.
2. Replace the two clusters with a larger cluster $a = C_1 \cup  C_2$.
3. Find the distance from $a$ to all other clusters.
4. Redo step 1 until you have a $2 \times2$ matrix, at which point you can join the last two clusters.




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
