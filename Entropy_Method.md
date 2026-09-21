# Entropy Method for Functions of Independent Random Variables

This note gives a corrected proof template for the entropy method in the product-space setting. The inputs $X_1,\ldots,X_n$ are independent, but the statistic

```math
Z=g(X_1,\ldots,X_n)
```

need not be a sum. The method replaces the usual MGF factorization for sums by **tensorization of entropy**.

The central pipeline is

```math
\text{independent coordinates}
\Longrightarrow
\text{entropy tensorization}
\Longrightarrow
\text{local sensitivity bound}
\Longrightarrow
\text{MGF bound}
\Longrightarrow
\text{Chernoff tail bound}.
```

Throughout, assume the needed exponential moments exist for the values of the MGF parameter under consideration.

---

## 1. Notation and entropy

Let $X_1,\ldots,X_n$ be independent random variables, and let

```math
Z=g(X_1,\ldots,X_n)
```

for a measurable real-valued function $g$.

For a positive random variable $Y$, define the entropy functional

```math
\operatorname{Ent}(Y)
:=
\mathbb E[Y\log Y]-(\mathbb EY)\log(\mathbb EY).
```

For each coordinate $i$, let $\mathbb E_i$ denote expectation with respect to $X_i$, holding all other coordinates fixed:

```math
\mathbb E_i[Y]
=
\mathbb E\bigl[Y\mid X_1,\ldots,X_{i-1},X_{i+1},\ldots,X_n\bigr].
```

The corresponding conditional entropy is

```math
\operatorname{Ent}_i(Y)
:=
\mathbb E_i[Y\log Y]
-
\mathbb E_i[Y]\log\mathbb E_i[Y].
```

There are two distinct coordinatewise comparison variables.

### Coordinate-deleted comparison: $Z_i$

Choose a measurable function $g_i$ of all variables except $X_i$, and write

```math
Z_i
=
 g_i(X_1,\ldots,X_{i-1},X_{i+1},\ldots,X_n).
```

Thus $Z_i$ is independent of $X_i$. This is the comparison used in the direct logarithmic-Sobolev inequality and in the self-bounding framework.

### Resampled comparison: $Z_i'$

Let $X_1',\ldots,X_n'$ be an independent copy of $X_1,\ldots,X_n$. Define

```math
Z_i'
=
 g(X_1,\ldots,X_{i-1},X_i',X_{i+1},\ldots,X_n).
```

This is the comparison used in symmetrization and resampling-sensitivity bounds.

---

## 2. Tensorization of entropy

If $Y=f(X_1,\ldots,X_n)>0$, then independence of the coordinates implies

```math
\operatorname{Ent}(Y)
\le
\sum_{i=1}^n\mathbb E\bigl[\operatorname{Ent}_i(Y)\bigr].
```

This is the tensorization inequality. In the discrete setting, it follows from Han's inequality for relative entropy. Conceptually, it replaces the product factorization of moment generating functions available for sums of independent random variables.

Tensorization applies to the positive random variable $Y=e^{sZ}$, not directly to an arbitrary possibly signed variable $Z$.

---

## 3. Entropy to the MGF

Define the uncentered MGF

```math
F(s)=\mathbb E[e^{sZ}].
```

Then

```math
\operatorname{Ent}(e^{sZ})
=
s\,\mathbb E[Ze^{sZ}]
-
\mathbb E[e^{sZ}]\log\mathbb E[e^{sZ}]
=
sF'(s)-F(s)\log F(s).
```

Therefore, a bound of the form

```math
\operatorname{Ent}(e^{sZ})
\le
Cs^2F(s)
```

implies

```math
\frac{d}{ds}\left(\frac{\log F(s)}{s}\right)
=
\frac{sF'(s)-F(s)\log F(s)}{s^2F(s)}
\le C.
```

Since

```math
\lim_{s\to0}\frac{\log F(s)}s=\mathbb EZ,
```

integration gives

```math
\log F(s)\le s\mathbb EZ+Cs^2.
```

Equivalently,

```math
\log\mathbb E\bigl[e^{s(Z-\mathbb EZ)}\bigr]\le Cs^2.
```

Chernoff's bound now yields

```math
\mathbb P(Z-\mathbb EZ\ge t)
\le
\exp(Cs^2-st).
```

Optimizing at $s=t/(2C)$ gives

```math
\mathbb P(Z-\mathbb EZ\ge t)
\le
\exp\left(-\frac{t^2}{4C}\right).
```

If the same MGF estimate holds for $-Z$, then

```math
\mathbb P(|Z-\mathbb EZ|\ge t)
\le
2\exp\left(-\frac{t^2}{4C}\right).
```

---

## 4. Coordinatewise logarithmic-Sobolev inequalities

Define

```math
\psi(u)=e^u-u-1.
```

For a coordinate-deleted comparison $Z_i$, tensorization plus a one-coordinate entropy estimate yields

```math
\operatorname{Ent}(e^{sZ})
\le
\sum_{i=1}^n
\mathbb E\left[
 e^{sZ}\psi\bigl(-s(Z-Z_i)\bigr)
\right].
```

A useful resampled version is

```math
\operatorname{Ent}(e^{sZ})
\le
\sum_{i=1}^n
\mathbb E\left[
 e^{sZ}\psi\bigl(-s(Z-Z_i')\bigr)
\right].
```

The latter is an inequality, not an equality with the tensorized conditional entropy terms.

For sharper one-sided estimates, define

```math
\tau(u)=u(e^u-1).
```

Using exchangeability of $X_i$ and $X_i'$, together with

```math
\psi(u)+e^u\psi(-u)=\tau(u),
```

one obtains the directional forms

```math
\operatorname{Ent}(e^{sZ})
\le
\sum_{i=1}^n
\mathbb E\left[
 e^{sZ}\tau\bigl(-s(Z-Z_i')\bigr)
 \mathbf 1_{\{Z>Z_i'\}}
\right],
```

and

```math
\operatorname{Ent}(e^{sZ})
\le
\sum_{i=1}^n
\mathbb E\left[
 e^{sZ}\tau\bigl(s(Z_i'-Z)\bigr)
 \mathbf 1_{\{Z<Z_i'\}}
\right].
```

The two directional inequalities are distinct. This is one reason upper- and lower-tail bounds can have different assumptions and constants.

---

## 5. Resampling framework: aggregate squared sensitivity

Assume that, for a deterministic constant $C>0$,

```math
\sum_{i=1}^n(Z-Z_i')^2\le C
\qquad\text{almost surely.}
```

For $s>0$, on the event $\{Z>Z_i'\}$, the number $x=s(Z-Z_i')$ is nonnegative. Since

```math
\tau(-x)=x(1-e^{-x})\le x^2
\qquad (x\ge0),
```

the upper-direction inequality gives

```math
\begin{aligned}
\operatorname{Ent}(e^{sZ})
&\le
s^2\mathbb E\left[
 e^{sZ}
 \sum_{i=1}^n (Z-Z_i')^2\mathbf 1_{\{Z>Z_i'\}}
\right] \\
&\le
s^2\mathbb E\left[
 e^{sZ}
 \sum_{i=1}^n (Z-Z_i')^2
\right] \\
&\le
Cs^2\mathbb E[e^{sZ}].
\end{aligned}
```

Thus

```math
\mathbb P(|Z-\mathbb EZ|>t)
\le
2\exp\left(-\frac{t^2}{4C}\right).
```

A bounded-differences condition

```math
|Z-Z_i'|\le c_i
\qquad\text{almost surely}
```

implies the squared-sensitivity condition with

```math
C=\sum_{i=1}^n c_i^2.
```

Hence the entropy-method proof gives

```math
\mathbb P(|Z-\mathbb EZ|>t)
\le
2\exp\left(-\frac{t^2}{4\sum_i c_i^2}\right).
```

This constant is not the sharp McDiarmid constant; it is the constant obtained from this particular entropy-method proof.

---

## 6. Self-bounding framework

The self-bounding framework uses $Z_i$, not the resampled variables $Z_i'$.

A nonnegative function $g$ is self-bounding if there exist coordinate-deleted functions $g_i$ such that, with

```math
Z_i=g_i(X_1,\ldots,X_{i-1},X_{i+1},\ldots,X_n),
```

we have almost surely

```math
0\le Z-Z_i\le1
\qquad\text{for every }i,
```

and

```math
\sum_{i=1}^n(Z-Z_i)\le Z.
```

A common generalization is the $(a,b)$-self-bounding condition

```math
0\le Z-Z_i\le1
\qquad\text{and}\qquad
\sum_{i=1}^n(Z-Z_i)\le aZ+b,
```

for constants $a,b\ge0$. The exact tail constants for this generalization depend on the theorem being invoked; they should not be mixed with the resampling theorem above.

### The paper's self-bounding theorem

Under the ordinary self-bounding assumptions, convexity of $\psi$, together with $\psi(0)=0$, implies that for $u\in[0,1]$,

```math
\psi(-su)\le u\psi(-s).
```

Therefore,

```math
\begin{aligned}
\operatorname{Ent}(e^{sZ})
&\le
\psi(-s)\mathbb E\left[e^{sZ}\sum_{i=1}^n(Z-Z_i)\right] \\
&\le
\psi(-s)\mathbb E[Ze^{sZ}].
\end{aligned}
```

Solving the resulting differential inequality gives

```math
\log\mathbb E\left[e^{s(Z-\mathbb EZ)}\right]
\le
\mathbb EZ\,\psi(s),
\qquad s\in\mathbb R.
```

Let

```math
h(u)=(1+u)\log(1+u)-u,
\qquad u\ge-1.
```

Chernoff optimization yields

```math
\mathbb P(Z\ge\mathbb EZ+t)
\le
\exp\left[-\mathbb EZ\,h\left(\frac{t}{\mathbb EZ}\right)\right],
\qquad t>0,
```

and, for $0<t\le\mathbb EZ$,

```math
\mathbb P(Z\le\mathbb EZ-t)
\le
\exp\left[-\mathbb EZ\,h\left(-\frac{t}{\mathbb EZ}\right)\right].
```

Using

```math
h(u)\ge\frac{u^2}{2+2u/3}
\quad (u\ge0),
\qquad
h(u)\ge\frac{u^2}{2}
\quad (-1\le u\le0),
```

gives the simpler bounds

```math
\mathbb P(Z\ge\mathbb EZ+t)
\le
\exp\left(-\frac{t^2}{2\mathbb EZ+2t/3}\right),
\qquad t>0,
```

and

```math
\mathbb P(Z\le\mathbb EZ-t)
\le
\exp\left(-\frac{t^2}{2\mathbb EZ}\right),
\qquad 0<t\le\mathbb EZ.
```

All displayed probability inequalities are upper bounds. Since $Z\ge0$, the lower-tail event is empty when $t>\mathbb EZ$.

---

## 7. General one-sided squared-sensitivity bound

The paper also proves a different result based on resampling. Suppose that, for constants $a,b>0$,

```math
\sum_{i=1}^n
(Z-Z_i')^2\mathbf 1_{\{Z>Z_i'\}}
\le aZ+b
\qquad\text{almost surely.}
```

Then, for $0<s<1/a$,

```math
\log\mathbb E[e^{s(Z-\mathbb EZ)}]
\le
\frac{s^2}{1-as}(a\mathbb EZ+b),
```

and consequently

```math
\mathbb P(Z>\mathbb EZ+t)
\le
\exp\left(-\frac{t^2}{4a\mathbb EZ+4b+2at}\right),
\qquad t>0.
```

This uses resampled variables $Z_i'$ and a one-sided squared-sensitivity condition. It is not the same theorem as the self-bounding result.

---

## 8. Reusable proof recipe

To apply the entropy method to a new statistic $Z=g(X_1,\ldots,X_n)$:

1. Identify the independent input coordinates.
2. Choose the comparison objects:
   - coordinate-deleted $Z_i$ for direct or self-bounding arguments; or
   - resampled $Z_i'$ for symmetrized sensitivity arguments.
3. Apply entropy tensorization to $Y=e^{sZ}$.
4. Use a coordinatewise logarithmic-Sobolev inequality to express entropy in terms of local changes.
5. Bound the aggregate local contribution using the structure of $g$.
6. Convert the entropy bound into a differential inequality for $F(s)=\mathbb E[e^{sZ}]$ or the centered log-MGF.
7. Integrate the differential inequality.
8. Apply Chernoff's bound and optimize in $s$.

The entropy method is a framework, not a single fixed concentration inequality. Different bounds on the coordinatewise perturbations produce different MGF estimates and therefore different tail regimes.
