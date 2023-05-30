**Remember, you can check the number of tensor products $\otimes$ as a sanity check for how many qubits are in your system. Addition *does not* increase the number of states, it simply lets you combine scalar multiples of states (e.g. $a\ket{0} + b\ket{0}$) or combine states from different computational bases (e.g. $a\ket{0} + b\ket{1}$).**


- Have notes on SWAP, Bell states, postulates, QFT images

![[Pasted image 20230527232421.png]]
Note how in the above image, **he uses the $\mapsto$ symbol with a superscript of a matrix to represent the gate being used.** 


Also, let us say we are measuring one of three qubits in a system. We use the $M_0$ measurement operator for the first qubit, and for the second two we use the identity. To denote this we can use: $P_o := \ket{0}\bra{0} \otimes I$. In this case, the $I$ denotes a $4 \times 4$ matrix, and doesn't necessarily need to denote a $2 \times 2$ matrix.



Had to find:

- Shor's algorithm (2010 p9 q11)
- Born rule