$\{P\}~C~\{Q\}$

This page us how to write assertations (state predicates, like P or Q above) and what they mean when writing out Hoare triples.

The lectures lay out the assertion syntax and semantics both informally and formally, these notes will just cover the formal definitions.


##### Assertions Syntax
Lecture 3 slide 17

$$\begin{align}

\mathcal{X} &::= X | x \\
t &::= \mathcal{X} | f(t_1, ..., t_n) ~n \geq 0\\
P, Q &::= \bot | \top | P \wedge Q | P \lor Q | P \Rightarrow  Q  \\
	&| \forall x.P | \exists x.P | t_1 = t_2 | p(t_1, ..., t_n) ~ n\geq0 \\
\lnot  &= P \Rightarrow \bot   

\end{align}
$$



##### Semantics of Terms (Move to language rules)

$[\![t]\!](s)$ defines the semantics of a term $t$ in a stack $s$:

$$\begin{align}

[\![-]\!](=)  & : \mathrm{Term} \times \mathrm{Stack} \rightarrow \mathbb{Z}  \\
[\![\mathcal{X}]\!](s)  & = s(\mathcal{X}) \\
[\![f(t_1, ..., t_n)]\!](s)  & = [\![f]\!]([\![t_n]\!](s),..., [\![t_n]\!](s)) \\
\end{align}
$$

In particular, if we have an expression term in a stack ($[\![E]\!](s)$), it is equivalent to evaluating the semantics of that expression $\mathcal{E}[\![E]\!](s)$. The stack acts as a parameter of the expression, which emphasises the fact that variables in the expression are free.

##### Semantics of Assertions

$$
\begin{align}
[\![-]\!] & : \mathrm{Assertion} \rightarrow \mathcal{P}(\mathrm{Stack}) \\
[\![\bot]\!] & = \{s \in \mathrm{Stack} | \bot \} = \emptyset   \\
[\![\bot]\!] & = \{s \in \mathrm{Stack} | \top \} = \mathrm{Stack} \\
[\![P \lor Q]\!] & = \{s \in \mathrm{Stack}| s \in [\![P]\!] \land s \in [\![Q]\!]\} = [\![P]\!] \cap [\![]\!]
\end{align}
$$


##### Substitution


##### Modified Program Variables

##### Free Variables

