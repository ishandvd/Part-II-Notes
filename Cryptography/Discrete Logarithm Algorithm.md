
##### Index Calculus Algorithm
Index Calculus Algorithm computes discrete logs in the cyclic group $Z_p^*$. Unlike the generic algos, it has sub-exponential runtime $2^{\mathcal{O}(\sqrt[]{\log p \log \log p})}$. So, prime $p$ bit-length in cyclic group $Z_p^*$ has to be MUCH longer to have the same security as the Index Calculus algorithm. With the Index Calculus algorithm, we can use a bit-length of just double the order $q$ of the subgroup.
![[Pasted image 20230529133051.png]]

The Index Calculus Algorithm can be used to solve the discrete logarithm problem on groups of the form Z ∗ p or subgroups thereof (e.g., Schnorr groups) and is significantly faster (time O(2 √ log p log log p )) than generic discrete-logarithm algorithms (e.g., the baby-step/giant-step algorithm) that work on any group G in time O( p |G|). For elliptic curve groups standardized for use in cryptography, no discrete-logarithm algorithms faster than O( p |G|) are known. As a result, to achieve e.g. 128-bit security, elliptic-curve groups can operate on 256-bit values, whereas Z ∗ p group operations must multiply values about 3072 bits long, making exponentiation much slower.


##### Schnorr Groups Proof

let 