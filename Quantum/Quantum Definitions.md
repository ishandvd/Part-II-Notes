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
Using shared entanglement as a resource that allows a qubit to be transmitted using two bits.

##### Superdense Coding
Using shared entanglement as a resource that allows two bits to be transmitted using a single qubit.

##### Quantum Key Distribution
Creating a one-time pad without Alice and Bob meeting or sharing an absolutely secure communication channel.

##### One-time pad

A list of $n$ random bits $r$. This computationally guarantees security.

##### BB84 Protocol

A protocol used for creating one-time pads.

##### Eavesdropping

Eavesdropping disturbs a shared key; when a third person (Eve) is listening in on a communication channel between Alice and Bob.


## Lecture 7

##### Deutsch-Jozsa Algorithm
##### Constant and Balanced

If a function returns the same output, it is constant. If it returns a uniform distribution of outputs, it is balanced.

##### Query complexity

In Deutsch’s algorithm we are not using a quantum computer to evaluate a “classically difficult” function per se, but rather using quantum phenomena to reduce the **number of queries** we need to make to an unknown function, to ascertain some information thereabout.

##### Oracles and Black Boxes

 When performing subroutines, we query $U$ in many quantum algorithms, which acts as a "black box". We assume that $U$ does the job as required, and that we can call on it as many times as required.


## Lecture 8

##### Quantum Parallelism
Exploiting the superposition of the computational basis states to do computation.

##### Quantum Search
Searching an unstructured database with N entries.

##### Grover's Algorithm
Quantum speedup by a quadratic factor in comparison to a classic computation.

## Lecture 9

##### Fourier Transform

Allows us to see the frequency components of signals. Useful for DSP.

The discrete Fourier transform (DFT) is still widely used. Takes an input vector $x$ and transforms it to an output $y$ of the same length, where y represents the frequencies within $x$:

$$
y_k = \frac{1}{\sqrt{ N }} \sum_{j=0}^{n-1} x_j e^{2\pi ij k / n}
$$


##### Quantum Fourier Transform
##### Quantum Phase Estimation

A subroutine at the hear of quantum chemistry and many important quantum algorithms. It allows us to determine the phase of the eigenvalues under a unitary matrix.


## Lecture 10


##### One-way function

Useful for public-key cryptography. If Alice publishes a public key, Bob can use it to encrypt a message to her. Alice can then use her private key to decrypt the message.

Relies on the asymmetry of the cryptography; easy to encrypt the message using the public key, hard to decrypt without knowing the private key. This relies on the existence of a one-way function.

**One-way functions** are easy to perform going forward, but hard to invert. e.g. RSA uses factoring as a one-way function.

These must be hard to invert ON AVERAGE, not just in the worstcase.

##### Shor's algorithm

Quantum algorithm that can factor numbers in polynomial time; best classical algorithm for this is the *number field sieve* which requires $\mathrm{exp}(\Theta^{1/3}\mathrm{log}^{2/3}n)$ operations, where $n =\mathrm{ceil}(\mathrm{log}_2N)$, i.e. the number of bits required to express N.

##### Ordering Finding

Finding $r$ such that $x^r~\mathrm{mod}~N=1$.

## Lecture 11

##### Quantum Simulation

Allows us to simulate the evolution of a physical simulation. 

##### Hamiltonian

A representation of the ground state energy of a physical system. The sum of all the energies e.g. graviational potential, kinetic.

##### Trotterisation

A method that allows us to do the following where $A$ is a matrix and not just a scalar (which is trivial):

$$
e^{A_1 + A_2} = e^{A_1} + e^{A_2} 
$$

##### Ground state energy

The smallest eigenvalue of the Hamiltonian $H$.


##### Variational quantum eigensolver

A method for finding the ground state energy by finding the smallest eigenvalue of the Hamiltonian.


## Lecture 12

##### Finite automata

- A set of $n_s$ states.
- An input alphabet of size $n_a$.
- A set of state transitions: usually represented in the form of a $n_s \times n_s$ matrix for each of the $n_a$ letters.
- An initial "start" state.
- An "accept" state (marked by a black circle).

The *accepted language* is the set of strings of letters from the alphabet s.t. the final state is the "accept" state.


##### Deterministic Finite Automata

For each state-letter pair, there is only one outgoing arrow. I.e., given an input string, we will finish at the same state every time.

##### Nondeterministic finite automata

Can have any number of outgoing arrows for each state-letter pair.

##### Probabilistic Automata

Essentially Markov chains, with state transitions being probabilistic; The transition matrix contains fractional values such that each column sums to one ($\sum_{b_i \in \mathrm{Outgoing~of~a}} p(a \to b_i) = 1$). 

##### Quantum Automata

The transition matrices are unitary matrices consisting of positive and negative complex numbers. A special quantum automata are *reversible automata* where transition matrices are binary permutation matrices (exactly one 1 in each column and row).



##### Turing Machines

A Deterministic Finite Automata. There is an infinitely long read-write tape, upon which the input string is initially written. At any time a “head” is over one space on the tape, and can read the symbol written there (initially the head is at the left-hand end of the tape). The action of a Turing machine is thus: 

At a given time, the DFA is in a certain state, and the head is over a symbol which it reads. Given this state-symbol pair, a transition function determines: 
- Which symbol to overwrite on the current space on the tape. 
- Whether to move the head left or right. 
- Which next state the DFA moves to. A Turing machine accepts the input if it halts in an accept state. 

The Turing machine is a sufficiently general model for computation to capture entirely that which can reasonably be thought of as mathematically computable. 
![[QFA.svg | center]]

	
##### Nondeterministic Turing Machines

If instead of a single action (overwritten symbol, move left or right and state transition) we allow a set of possible actions, then we get the nondeterministic Turing machine.

This can be thought of as a tree, where each branching process represents the variety of possible actions at a given time. A string is accepted if there is some path through the tree to an accept state.

##### Quantum Turing Machines

Quantum Turing machines are like probabilistic Turing machines, but now complex amplitudes are associated with each possible next move. It is also necessary that the linear transformation defined by the machine is unitary.


##### Complexity Classes

- **P**: The class of problems that can be decided in polynomial-time on a Turing machine.
- **NP**: The problems that can be solved by a [[Quantum Definitions#Nondeterministic Turing Machines|Nondeterministic Turing Machine]] that has a tree height bounded polynomially. **P** represents problems that can be solved using only one specific branch (root -> leaf). Therefore $P \subseteq NP$.
- **BPP**: The set of languages, $L$, for which there is a probabilistic Turing machine, $M$, running in polynomial time with:$$
P(M~\mathrm{accepts}~w) = \left\{
\begin{array}{ll}
	> \frac{2}{3}~\mathrm{if}~w \in L \\
	< \frac{1}{3}~\mathrm{if} w \notin L
\end{array}
\right.
$$Clearly each probability distribution in a probabilistic Turing machine could consist of a single deterministic branch, so $P \subseteq BPP$.
- **BQP**: The set of languages, $L$, for which there is a [[Quantum Definitions#Quantum Turing Machines|quantum Turing machine]], $M$, running in polynomial time with: The choice of $\frac{2}{3}$ is arbitrary; it should be fine as long as we pick a limit $> \frac{1}{2}$. The quantum Turing machine generalises the probabilistic Turing machine, so $BPP \subseteq BQP$. 
- Don't know if $P = NP$.
- Conjectured that $P = BPP$, but we don't know whether $BPP$ is a subset of $NP$.
- As factoring is thought to be super-polynomial (ALMOST exponential), the existence of Shor's algorithm is taken as evidence that $BPP \neq BQP$.
- Widely believed that $NP$-complete problems cannot be solved in polynomial time on a quantum computer (unless $P = NP$), so $NP \nsubseteq BQP$.
- ... Also believed there are problems OUTSIDE of $NP$ which can be solved in polynomial time on a quantum computer, so $BQP \nsubseteq NP$.

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
