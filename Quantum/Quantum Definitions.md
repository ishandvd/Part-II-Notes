## Lecture 1

##### Classical Bit

Similar to how we use 0 and 1 in all other computing, we have:

$$
0 = \begin{bmatrix}
1 \\ 0
\end{bmatrix},
1 = \begin{bmatrix}
0 \\ 1
\end{bmatrix}
$$


##### Qubit

$$
0 = \begin{bmatrix}
1 \\ 0
\end{bmatrix} = \ket{0}  , 1 = \begin{bmatrix}
0 \\ 1
\end{bmatrix} = \ket{1} 
$$
$$
\ket{\psi} = \alpha\ket{0} + \beta\ket{1}
$$
##### Measurement (Born Rule)
Measuring a qubit with state $\alpha\ket{0} + \beta\ket{1}$ results in $\ket{0}$ with probability $\begin{vmatrix}\alpha\end{vmatrix}^2$ and $\ket{1}$ with probability  $\begin{vmatrix}\beta\end{vmatrix}^2$ . A

##### Hadamard Gate

Introduces superposition to a qubit in the computation basis state.

$$
H = \frac{1}{\sqrt{ 2 }}\begin{bmatrix}
1 & 1 \\
1 & -1
\end{bmatrix}
$$
Has the following effect on the computation basis states:
$$
H \ket{+} \to \ket{0}
$$
$$
H \ket{-} \to\ket{1} 
$$

##### Entanglement

When two particles link together in a certain way no matter how far apart they are in space.

##### Bell State

Each of the two qubits in the bell state are in equal superposition, however the two qubits are entangled. As soon as one qubit is measured, the second qubit collapses into the same state. 

$$
\ket{\phi^+} = \frac{1}{\sqrt{ 2 }} (\ket{00}  + \ket{11} )
$$

##### Superposition

If a physical system may be in one of many arrangements of particles or fields, then the most general state is a combination of all these possibilities, or, a **superposition** of these.

##### Interference
When a subatomic particles interact with and influence themselves and other particles while in a probabilistic superposition state.


## Lecture 2

##### Hilbert Space

Finite dimension vector space with a defined inner product.

##### Adjoint

$$ \begin{align}


\mathrm{if}~A = \begin{bmatrix}
a_{11} & \dots & a_{1m} \\
\vdots  & \ddots  & \vdots  \\
a_{n1} &  & a_{nm}
\end{bmatrix}, \\
A^{^{\dagger}} = (A^*)^T = \begin{bmatrix}
a_{11}^* & \dots & a_{n1}^* \\
\vdots  & \ddots  & \vdots  \\
a_{1m}^* &  & a_{mn}^*
\end{bmatrix}
\end{align}
$$

##### Dirac Notation

Bra: $$
\bra{\phi} = \begin{bmatrix}
a_1 & a_2 & \dots & a_n
\end{bmatrix}
$$
Ket: 

$$
\ket{\phi} = \begin{bmatrix}
a_1 \\
a_2 \\
\vdots \\
a_n \\
\end{bmatrix}
$$

##### Inner and Outer Product

Inner product:

$$
\bra{u} \ket{v} = \bra{u} \times\ket{v} = \begin{bmatrix}
a_1^* & ... & a_n^*
\end{bmatrix} \begin{bmatrix}
b_1 \\
\vdots \\
b_n
\end{bmatrix}
= \sum_{i=1}^n a_1^*b_i
$$

if $\bra{u}\ket{v} = 0$ then $\ket{u}$ and $\ket{v}$ are **orthogonal**.

$|\ket{u}||= \sqrt{ \bra{u}\ket{u} }$ is the **norm** of $\ket{u}$; all unit vectors have norm = 1.

Outer product:

$$
\ket{u} \bra{v}  = \begin{bmatrix}
a_1 \\
\vdots   \\
a_n
\end{bmatrix} \begin{bmatrix}
b_1^* & \dots & b_m^*
\end{bmatrix} = \begin{bmatrix}
a_1b_1^*  &  \dots & a_1b_m^* \\
\vdots & \ddots &  \\
a_nb_1^* &  & a_nb_m^*\\

\end{bmatrix}
$$

##### Projector

If $\ket{u}$ is a unit vector, then $\ket{u}\bra{u}$ is know as a project, as $\ket{u}\bra{u}$ is an operator that "projects" an arbitrary vector (of appropriate dimension) $\ket{v}$ onto the subspace $\ket{u }$.

##### Basis

A basis of $\mathbb{C}^n$ is a minimal collection of vectors $\ket{v_1}, \ket{v_2}, ..., \ket{v_n}$ such that every vector $\ket{v} \in \mathbb{C}^n$ can be expressed as a linear combination of these:

$$
\ket{v}  = \alpha_1 \ket{v_1}  + \alpha_2 \ket{v_2}  + \dots+ \alpha_n \ket{v_n}
$$
where the coefficients $\alpha_i \in \mathbb{C}$ . 

That is, the basis is a minimal collection of vectors where they are all linearly independent; no $\ket{v_i}$ can be expressed as a linear combination of the others. The size of the basis is $n$, termed its **dimension**.

##### Eigenvectors and Eigenvalues
##### Hermitian
##### Unitary


## Lecture 3

##### State Space
##### Evolution
##### Pauli Matrices
##### Measurement
##### Phase
##### Entangled States


## Lecture 4

##### Helstrom-Holevo Bound
##### No-signalling principle
##### No-cloning principle
##### No-deleting principle


## Lecture 5

##### Tensor network
##### Quantum Circuit
##### SWAP
##### CNOT
##### Universal Gate Set
##### Toffoli

## Lecture 6

##### Teleportation
##### Superdense Coding
##### Quantum Key Distribution
##### One-time pad
##### BB84 Protocol
##### Eavesdropping


## Lecture 7

##### Deutsch-Jozsa Algorithm
##### Constant and Balanced
##### Query complexity
##### Oracles and Black Boxes


## Lecture 8

##### Quantum Search
##### Grover's Algorithm


## Lecture 9

##### Fourier Transform
##### Quantum Fourier Transform
##### Quantum Phase Estimation



## Lecture 10


##### One-way function
##### Shor's algorithm
##### Ordering Finding


## Lecture 11

##### Quantum Simulation
##### Hamiltonian
##### Trotterisation
##### Ground state energy
##### Variational quantum eigensolver

## Lecture 12

##### Finite automata
##### Deterministic Finite Automata
##### Nondeterministic finite automata
##### Probabilistic Automata
##### Quantum Automata
##### Turing Machines
##### Nondeterministic Turing Machines
##### Quantum Turing Machines
##### Complexity Classes


## Lecture 13

##### Quantum Error Correction
##### Three-bit repetition code
##### Three-qubit bit-flip code
##### Three-Qubit phase-flip code
##### Depolarising Channel



## Lecture 14

##### Fault Tolerance
##### Steane Code Gates
##### Transversatility
##### Concatenated Codes

## Lecture 15

##### Quantum Adiabatic Theorem
##### Metaheuristics
##### Exploration vs Exploitation
##### Quantum Annealing
##### Quantum Tunneling
##### D-Wave

## Lecture 16

##### NISQ
##### Quantum Counting
##### HHL 
##### Quantum Singular-Value Transform
##### Quantum Machine Learning
##### Quantum Volume
