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

If a $n \times n$ matrix, **A**, has the effect of scaling a given non-zero vector $\ket{v}$ by a constant $\lambda$, then that vector is known as an eigenvector, with corresponding eigenvalue $\lambda$: 

$$
A \ket{v}  = \lambda\ket{v}
$$
The eigenvalues of a matrix are the roots of the characteristic polynomial: 

$$
\mathrm{det}(A - \lambda I) = 0
$$
Where $\mathrm{det}$ denotes the determinant, and $I$ is the $n \times n$ identity. Each square matrix has ATLEAST ONE eigenvalue.

##### Hermitian

A matrix is *Hermitian* if $A = A^{^{\dagger}}$. 

##### Unitary

When $A^{^{\dagger}}A = AA^{^{\dagger}} = I$ .

## Lecture 3

##### State Space

The [[Quantum Definitions#Hilbert Space]] that a state lives in (in the context of an isolated physical system) is known as the state space.


##### Evolution

How a system changes over time; useful for describing what the Hamiltonian is for example when doing chemistry.

##### Pauli Matrices

X, Y, Z are important one-qubit unitary matrices:

$$
X = \begin{bmatrix}
0 & 1 \\
1 & 0
\end{bmatrix}, Y = i\begin{bmatrix}
0 & -1 \\
1 & 0
\end{bmatrix}, Z = \begin{bmatrix}
1 & 0  \\
0 & -1
\end{bmatrix}
$$

X is akin to a NOT gate:

$$
X\ket{0}  = \ket{1}, X\ket{1} = \ket{0}   
$$

Y has the following effect:

$$
Y\ket{0} = i\ket{1} , Y\ket{1}  = i-\ket{0}
$$
Z has the following effect:

$$
Z\ket{0} = \ket{0}, Z\ket{1}, = - \ket{1}
$$

##### Phase

One-bit qubits can be written as:

$$
\ket{\psi} = e^{i \theta}(\alpha \ket{0}  + \beta ^{i \theta}\ket{1} ) \equiv e^{i \theta}\ket{\psi^`} 

$$
$\theta$ is known as the **global phase**. It has no impact when a unitary $U$ is applied.

When doing a measurement with the measurement operator $P_m$: 

$$
\begin{align}
\bra{\psi} P_m^{^{\dagger}}P_M \ket{\psi}  = \bra{\psi^`}e^{-i \theta}   p_m^{^{\dagger}}P_m e_{i \theta}  \ket{\psi^`} = \bra{\psi^ `}    
\end{align}P_m^{^{\dagger}}P_m \ket{\psi^`} 
$$


##### Entangled States

We can use the CNOT to get us into an entangled state:

$$
\mathrm{CNOT}(\ket{+} \otimes \ket{0} ) = \frac{1}{\sqrt{ 2 }}(\ket{00}  + \ket{11} )
$$

This cannot be separated as a tensor product of two qubits. We call CNOT an entangling gate.

## Lecture 4

##### Helstrom-Holevo Bound

The formalisation behind the fact that we cannot perfectly distinguish between two non-orthogonal quantum states.

##### No-signalling principle

When measuring one of two entangled qubits, the other collapses, meaning quantum states display non-local behaviour. (Einstein: "spooky action at a distance"). However, we cannot use this to transfer information faster than the speed-of-light, which would violate the theory of relativity.

Collapsing entanglement cannot be used to transfer information, as proven by the no-signalling principle.

##### No-cloning principle

We cannot clone qubits.

##### No-deleting principle

We cannot delete one of two copies of a quantum state, that is, there is no unitary $U$ such that:

$$
U(\ket{\psi} \ket{\psi} ) = \ket{\psi} \ket{0}
$$
More generally, quantum computing is reversible.


## Lecture 5

##### Tensor network

We can apply separable operations even to entangled states using tensor networks, where each wire represents a qubit.

##### Quantum Circuit

Wire a qubits (possible entangled), gates are unitary matrices (e.g. $X,Y,Z$).

##### SWAP

Let $\ket{\psi_1}\ket{\psi_2} = \alpha\ket{00} + \beta\ket{01} + \gamma\ket{10} + \delta\ket{11}$, which corresponds to vector: $[\alpha, \beta, \gamma, \delta]^T$. We have:

$$
\mathrm{SWAP} = \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}, \begin{bmatrix}
\alpha \\
\beta \\
\gamma \\
\delta \\

\end{bmatrix} = \mathrm{SWAP} \begin{bmatrix}
\alpha \\
\gamma \\
\beta \\
\delta \\

\end{bmatrix}
$$
SWAP can be constructed from three CNOT gates.

##### CNOT

A Controlled Not gate that acts on two qubits.

##### Universal Gate Set

Solovay-Kitaev theorem implies that any circuit containing m CNOTs and arbtrary single qubit unitaries can be approximated to an accuracy $\epsilon$ by a circuit using a universal finite gate-set with $\mathcal{O}(m\mathrm{log}^c(m / \epsilon))$ gates where $c \approx2$. 

Only THREE GATES are needed for a universal gat-set. CNOT, H, and:

$$
T = \begin{bmatrix}
1 & 0 \\
0 & e^{i \pi/4}
\end{bmatrix}
$$

**Gottesman-Knill** theorem holds that any circuit containing just X,Y,Z,H,S, and CNOT can be efficiently simulated on a classical computer.

$$
\begin{align}
S  & = T^2 \\
Z  & = S^2 \\
X  & = HZH \\
Y  & = iXZ = SXSZ \\
\end{align}$$





##### Toffoli

A quantum generalisation of the AND gate. It is a CNOT that acts on two inputs.

## Lecture 6

##### Teleportation
Using shared entanglement as a resour ce

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
