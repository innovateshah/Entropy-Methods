# Entropy-Methods
Research in Randomized Algorithms


```math
\begin{aligned}
\text{Ent}[f] = \mathbb{E}[f\log f] - \mathbb{E}[f]\log\mathbb{E}[f]
\end{aligned}
```

```math
Z = g(X_1,X_2,\dots,X_n), \quad X_i \text{ are indepenet}
```

```math
E_i[Z]
= \mathbb{E}\left[Z \mid \text{fix all } X_j,\ j\neq i\right]
```

```math
\text{Ent}[Z]
< \sum_i \mathbb{E}\left[\text{Ent}_i[Z]\right]
```

### Goal

```math
\text{Ent}[e^{sZ}]
< K s^2 \mathbb{E}[e^{sZ}]
```

Assume that the inequality holds.

```math
F(s)=\mathbb{E}[e^{sZ}]
```

```math
\begin{aligned}
\text{Ent}[e^{sZ}]
&=sF'(s)-F\log F \\
&< Ks^2F(s)
\end{aligned}
```

```math
\frac{1}{s}\frac{F'}{F}
+\left(-\frac{1}{s^2}\right)\log F
<K
```

```math
\frac{d}{ds}\left(\frac{\log F}{s}\right)<K
```

```math
\frac{\log F}{s}<Ks+\mathbb{E}Z=Ks,
\qquad
\text{by shifting } Z \text{ by the mean of } Z.
```

```math
F\leq e^{Ks^2}
```

```math
\Pr[e^{sZ}>e^{st}]
\leq \frac{\mathbb{E}e^{sZ}}{e^{st}}
\leq e^{Ks^2-st}
```

```math
s=\frac{t}{2K},
\qquad
\text{optimizes the bound}
```

```math
e^{-Ct^2}
```

---

Now we can try to derive the inequality

```math
\text{Ent}<Ks^2F(s)
```

```math
X'_i \text{ same in distribution to } X_i
\text{ but independent}
```

```math
\psi(x)=e^x-x-1\sim\frac{x^2}{2}
```

```math
Z'_i=g(X_1,\ldots,X'_i,\ldots,X_n)
```

```math
\begin{aligned}
\text{Ent}[Z]
&<\sum_i\mathbb{E}[\text{Ent}_i[Z]] \\
&=\sum_i\mathbb{E}\left[
e^{sZ}\psi\left(-s(Z-Z'_i)\right)
\right]
\end{aligned}
```

two case \(Z>Z'_i\) and another where \(Z'_i>Z\).

```math
\tau=x(e^x-1)
```

```math
\leq
\sum_i
\mathbb{E}\left[
e^{sZ}
\tau\left(-s(Z-Z'_i)\right)
\mathbf{1}_{Z>Z'_i}
\right]
```

```math
\tau(-x)\leq x^2
\qquad\text{for }x>0
```

```math
\sum_i
\mathbb{E}\left[
e^{sZ}s^2(Z-Z'_i)^2
\mathbf{1}_{Z>Z'_i}
\right]
```

Assume

```math
(Z-Z'_i)^2<c_i
```

for all inputs \(X\).

```math
\begin{aligned}
&\leq
s^2\mathbb{E}[e^{sF}]
\left(\sum_i c_i\right) \\
&=\left(\sum_i c_i\right)s^2F(s)
\end{aligned}
```

qed.

### Self bounding functions.

Here we redefine $Z_i'$. Again the impor
```math
Z_i' = \text{inf}_{X'_i} g(X_1...X_{i-1},X_{i}',X_{i+1}...X_n)
```

We call (a,b)-self bounding if the following holds
```math
\sum_i Z-Z'_i\leq aZ+b
```

Then we can say

```math
\Pr[>t]
\geq
e^{-\frac{t^2}{2(a\mathbb{E}Z+b+at)}}
```

```math
\Pr[Z-\mathbb{E}Z<-t]
\geq
e^{-\frac{t^2}{2(a\mathbb{E}Z+b+t/3)}}
```
