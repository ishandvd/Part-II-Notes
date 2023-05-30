#### Teleportation

#### Superdense Coding

#### Quantum Key Distribution

#### Deutch's Algorithm


#### Grover's Algorithm

#### Quantum Fourier Transform

#### Inverse Quantum Fourier Transform

#### Quantum Phase Estimation

#### Shor's Factoring Algorithm

#### Order Finding

#### Variational Quantum Eigensolver

#### Three-Qubit Bit-Flip Code

#### Three-Qubit Phase-Flip Code

#### Shore Codes

![[Pasted image 20230530190313.png]]

This encodes the computational basis states $\ket{0}, \ket{1}$ as:

$$
\begin{align}
\ket{0} &\to \ket{0_L} = \frac{1}{2\sqrt{2}}(\ket{000} + \ket{111})(\ket{000} + \ket{111})(\ket{000} + \ket{111}) \\
\ket{1} &\to \ket{1_L} = \frac{1}{2\sqrt{2}}(\ket{000} - \ket{111})(\ket{000} - \ket{111})(\ket{000} - \ket{111})  
\end{align}$$

And an arbitrary:
$$
\begin{align}
\alpha\ket{0} + \beta\ket{1} \to \frac{1}{2\sqrt{2}}(\alpha(\ket{000} + \ket{111})(\ket{000} + \ket{111})(\ket{000} + \ket{111}) \\+ \beta(\ket{000} - \ket{111})(\ket{000} - \ket{111})(\ket{000} - \ket{111})) 
\end{align}
$$

If the first qubit has an error which takes $\ket{0} \to a \ket{0} + b \ket{1}$ and $\ket{1} \to c \ket{0} + d \ket{1}$, then we have the state:


$$
\begin{align}
\frac{1}{2\sqrt{2}}(\alpha(a\ket{000} + b\ket{100} + c  + \ket{111})(\ket{000} + \ket{111})(\ket{000} + \ket{111}) \\+ \beta(\ket{000} - \ket{111})(\ket{000} - \ket{111})(\ket{000} - \ket{111})) 
\end{align}
$$