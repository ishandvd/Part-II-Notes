
##### Index Calculus Algorithm
Index Calculus Algorithm computes discrete logs in the cyclic group $Z_p^*$. Unlike the generic algos, it has sub-exponential runtime $2^{\mathcal{O}(\sqrt[]{\log p \log \log p})}$. So, prime $p$ bit-length in cyclic group $Z_p^*$ has to be MUCH longer to have the same security as the Index Calculus algorithm. With the Index Calculus algorithm, we can use a bit-length of just double the order $q$ of the subgroup.
![[Pasted image 20230529133051.png]]

##### Schnorr Groups Proof

let 