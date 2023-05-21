This tells us how to write a program.

### Syntax of $\mathrm{WHILE}$

**Arithmetic Expressions**
```
E ::== N | X | E1 + E2
	| E1 - E2 |  E1 x E2
```

**Boolean Expressions**
```
B ::= T | F | E1 = E2
	| E1 <= E2 | E1 >= E2
```

**Commands**

```
C ::= skip
	| C1; C2
	| X := E
	| if B then C1 else C2
	| while B do C
```

**Substitution**
```
 _ [_ / _] : Expr x Expr x Var -> Expr

N[E2/X] = N
Y[E2/X] = if Y = X: E2 else Y
(Ea + Eb)[E2/X] = (Ea[E2/X]) + (Eb[E2/X]) 

- Same for - and x operators.
```



### Syntax of $\mathrm{WHILE}_P$

**Arithmetic Expressions**
```
null = 0
```



**Commands**
```
 C ::= skip | C1;C2 | X := E
	 | if B then C1 else C2
	 | while B do C
	 | X := [E] 
	 | [E1] := E2
	 | X := alloc(E0, ... , En)
	 | dispose(E)
```


Where `X := [E]` means set var X to the value at pointer E and `[E1] := E2` means set the value pointed to by E1 to E2.


### Implementations

**Cpush**
```
Cpush:  Y := HEAD; HEAD := alloc(X,Y)
```

**Cmax**
```
Cmax: 
	X := [HEAD + 1]; M := [HEAD];
	while X != null do
		E := [X];
		if E > M then M := E else skip;
		X := [X + 1];
```


**Merge**
``` Merging lists X and Y. Assuming they're both sorted.
Z := alloc(0, null); P := Z;
while X != null and Y != null do
	(U := [X]; V := [Y];
	 if U <= V then ([P + 1] := X; X := [X + 1])
	 else ([P + 1] := Y; Y := [Y + 1]);
	 P := [P + 1])

if X = null then ([P + 1] := Y; Y := null)
else ([P + 1] := X; X := null);
P := [Z + 1]; dispose(Z); dispose(Z + 1); Z := P
```


**Factorial**
```
while X != 0 do
	Y := Y x X;
	X := X - 1;
```

**Integer Square Root**
```
S = 0;
while (S + 1) x (S + 1) <= X do
	S := S + 1
```