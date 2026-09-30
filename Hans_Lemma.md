# Han's Lemma

Let $X_1,\ldots,X_n$ be discrete random variables with finite joint entropy.

For a subset $S\subseteq[n]$, where $[n]=\{1,\ldots,n\}$, define $X_S=(X_i)_{i\in S}$.

Then for every integer $k$ satisfying $1\leq k\leq n$,

$$
\frac{1}{\binom{n}{k}}
\sum_{\substack{S\subseteq[n]\\|S|=k}}
H(X_S)
\geq
\frac{k}{n}H(X_1,\ldots,X_n).
$$

Equivalently,

$$
H(X_1,\ldots,X_n)
\leq
\frac{1}{\binom{n-1}{k-1}}
\sum_{\substack{S\subseteq[n]\\|S|=k}}
H(X_S).
$$

## Possible use for t-wise

As a reminder we choose
We simply choose $k=t$,
Then we only have to consider entropy of independent variables.
We look at

```math
\begin{align*}
f_S(X_S) = \mathbb{E}_Q[f(X) | X_S]
\\
\mathbb{Ent}_{Q_S}(f_S)
=
\mathbb{E}_{Q_S}[f_S\log f_S]
-
\mathbb{E}_Q[f]\log\mathbb{E}_Q[f]
\end{align*}
```






# Shearer's Lemma

**Shearer's lemma** is an entropy inequality stating that the joint entropy of a random vector is bounded by the appropriately normalized sum of the entropies of sufficiently overlapping coordinate projections.

It is a covering inequality: if every coordinate appears many times in a collection of coordinate subsets, then the sum of the local entropies contains at least that many copies of the global information.

---

## Standard statement

Let

```math
X=(X_1,\ldots,X_n)
```

be a discrete random vector, and let

```math
\mathcal A=\{A_1,\ldots,A_m\}
```

be a family of subsets of $[n]$. Suppose every coordinate $i\in[n]$ belongs to at least $r$ members of $\mathcal A$:

```math
\left|\{j:i\in A_j\}\right|\ge r.
```

Then Shearer's lemma states

```math
H(X_1,\ldots,X_n)
\le
\frac{1}{r}
\sum_{j=1}^m H(X_{A_j}),
```

where

```math
X_{A_j}=(X_i)_{i\in A_j}.
```

Here $H$ denotes Shannon entropy:

```math
H(X)=-\sum_x \Pr[X=x]\log \Pr[X=x].
```

The logarithm may have any fixed base, provided it is used consistently.

If every coordinate belongs to exactly $r$ sets, this is the usual exact-$r$-cover version. The at-least-$r$ version follows by viewing the family as an $r$-fold cover.

---
## Proof

Order the coordinates as $1,\ldots,n$. By the entropy chain rule,

```math
H(X_1,\ldots,X_n)
=
\sum_{i=1}^n
H(X_i\mid X_1,\ldots,X_{i-1}).
```

For any $A\subseteq[n]$, define

```math
A_{ < i } = A \cap \{ 1,\ldots,i-1 \}
```

Applying the chain rule to the subvector $X_A$ gives

```math
H( X_A ) = \sum_{ i \in A } H ( X_i \mid X_{ A, < i } )
```


Since conditioning reduces entropy and

```math
X_{ A,i }
```

contains no more information than the complete preceding tuple

```math
(X_1,\ldots,X_{i-1}),
```

we have

```math
H(X_i\mid X_{A, < i })
\ge
H(X_i\mid X_1,\ldots,X_{i-1}).
```

Consequently,

```math
H(X_A)
\ge
\sum_{i\in A}
H(X_i\mid X_1,\ldots,X_{i-1}).
```

Summing this inequality over $A_1,\ldots,A_m$ yields

```math
\sum_{j=1}^m H(X_{A_j})
\ge
\sum_{i=1}^n
\left|\{j:i\in A_j\}\right|
H(X_i\mid X_1,\ldots,X_{i-1}).
```

Every coordinate appears at least $r$ times, so

```math
\sum_{j=1}^m H(X_{A_j})
\ge
r\sum_{i=1}^n
H(X_i\mid X_1,\ldots,X_{i-1}).
```

Using the chain rule once more,

```math
\sum_{j=1}^m H(X_{A_j})
\ge
rH(X_1,\ldots,X_n).
```

Dividing by $r$ proves Shearer's lemma.

---

## Han's inequality

A particularly important special case takes the leave-one-out sets

```math
A_i=[n]\setminus\{i\},
\qquad i=1,\ldots,n.
```

Each coordinate belongs to exactly $n-1$ of these sets. Shearer's lemma becomes

```math
H(X_1,\ldots,X_n)
\le
\frac{1}{n-1}
\sum_{i=1}^n
H(X_1,\ldots,X_{i-1},X_{i+1},\ldots,X_n).
```

This is commonly called **Han's inequality**.

---

## Fractional Shearer's lemma

A more general weighted version uses a fractional cover. Let $\mathcal A$ be a family of subsets of $[n]$ and assign each $A\in\mathcal A$ a weight $\alpha_A\ge0$. Assume

```math
\sum_{A\ni i}\alpha_A\ge1
\qquad\text{for every }i\in[n].
```

Then

```math
H(X_1,\ldots,X_n)
\le
\sum_{A\in\mathcal A}\alpha_A H(X_A).
```

The ordinary $r$-cover statement is recovered by assigning every selected set the common weight

```math
\alpha_A=\frac{1}{r}.
```

Fractional Shearer's lemma is often the natural form for hypergraph-cover arguments, entropy proofs for read-$k$ families, graphical models, and combinatorial counting arguments.

## Generalization to sub-modular functions

Shear lemma also holds for sub modular functions.

