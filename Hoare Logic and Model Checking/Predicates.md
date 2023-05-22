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
[\![P \lor Q]\!] & = \{s \in \mathrm{Stack}| s \in [\![P]\!] \lor s \in [\![Q]\!]\} = [\![P]\!] \cap [\![Q]\!] \\
[\![P \lor Q]\!] & = \{s \in \mathrm{Stack}| s \in [\![P]\!] \land s \in [\![Q]\!]\} = [\![P]\!] \cup [\![Q]\!] \\
[\![P \Rightarrow Q]\!] & = \{s \in \mathrm{Stack}| s \in [\![P]\!] \Rightarrow s \in [\![Q]\!]\}
\end{align}
$$
![[Pasted image 20230522182522.png]]

The predicate $[\![p]\!]$ associated to each predicate symbol $p$ is provided along with the implicit signature.

$s \models P$ is equivalent to $s \in [\![P]\!]$ .

The predicate function $p(t_1, ..., t_n)$ is assumed to be provided along with the implicit signature.

##### Substitution

Our quantifiers $\forall , \exists$ bind logical variables (that is, auxiliary variables like ($x,y$), and all free variables in expression E are program variables (like $X,Y$). Therefore there is no problem with variable capture when using the quantifiers as described in the [[Predicates#Semantics of Assertions|Semantics of Assertions]] section.

- $[\![t[E/X]]\!](s) = [\![t]\!](s[X \mapsto \mathcal{E}[\![E]\!](s)])$
	That is, the set of predicate terms $t$ that agree with the stack $s$ when substituting all occurrences of X with E is equivalent to the set of predicate terms $t$ that are valid when we set the value of the program variable $X$ to the evaluated expression E ($\mathcal{E}[\![E]\!](s)$).

	This can be proven by induction on t by using the substitution property for expressions.
- $s \in [\![P[E/X]]\!] \Leftrightarrow s[X \mapsto \mathcal{E}[\![E]\!](s)] \in [\![P]\!]$
	Meaning, if $s$ is in the set of valid predicates $P$ with X substituted with E, then $s$ with the value of the program variable $X$ set to the evaluated expression E ($\mathcal{E}[\![E]\!](s)$) is in the set of valid predicates $P$ (where $P$ has no substitutions).
	The inverse implication also applies.

Both of these can be proven by induction on t and P respectively.
 
##### Modified Program Variables

##### Free Variables

