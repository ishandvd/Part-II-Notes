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



##### Semantics of Terms

$[\![t]\!](s)$ defines the semantics of a term $t$ in a stack $s$:

$$\begin{align}

[\![-]\!](=)  & : \mathrm{Term} \times \mathrm{Stack} \rightarrow \mathbb{Z}  \\
[\![\mathcal{X}]\!](s)  & = s(\mathcal{X}) \\
[\![f(t_1, ..., t_n)]\!](s)  & = [\![f]\!]([\![t_n]\!](s),..., [\![t_n]\!](s)) \\

\end{align}
$$



##### Semantics of Assertions


##### Substitution


##### Modified Program Variables

##### Free Variables

