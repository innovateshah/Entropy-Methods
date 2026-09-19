# Entropy-Methods
Research in Randomized Algorithms


$$
\operatorname{Ent}[f]
= \mathbb{E}[f\log f]
- \mathbb{E}[f]\log\mathbb{E}[f]
\leq \int |\operatorname{Gradient} f|^2
$$

$$
Z = g(X_1,X_2,\dots,X_n), \quad X_i \text{ are indepenet}
$$

$$
E_i[Z]
= \mathbb{E}\left[Z \mid \text{fix all } X_j,\ j\neq i\right]
$$

$$
\operatorname{Ent}[Z]
< \sum_i \mathbb{E}\left[\operatorname{Ent}_i[Z]\right]
$$

### Goal

$$
\operatorname{Ent}[e^{sZ}]
< K s^2 \mathbb{E}[e^{sZ}]
$$

Assume that the inequality holds.

$$
F(s)=\mathbb{E}[e^{sZ}]
$$

$$
\begin{aligned}
\operatorname{Ent}[e^{sZ}]
&=sF'(s)-F\log F \\
&< Ks^2F(s)
\end{aligned}
$$

$$
\frac{1}{s}\frac{F'}{F}
+\left(-\frac{1}{s^2}\right)\log F
<K
$$

$$
\frac{d}{ds}\left(\frac{\log F}{s}\right)<K
$$

$$
\frac{\log F}{s}<Ks+\mathbb{E}Z=Ks,
\qquad
\text{by shifting } Z \text{ by the mean of } Z.
$$

$$
F\leq e^{Ks^2}
$$

$$
\Pr[e^{sZ}>e^{st}]
\leq \frac{\mathbb{E}e^{sZ}}{e^{st}}
\leq e^{Ks^2-st}
$$

$$
s=\frac{t}{2K},
\qquad
\text{optimizes the bound}
$$

$$
e^{-Ct^2}
$$

---

Now we can try to derive the inequality

$$
\operatorname{Ent}<Ks^2F(s)
$$

$$
X'_i \text{ same in distribution to } X_i
\text{ but independent}
$$

$$
\psi(x)=e^x-x-1\sim\frac{x^2}{2}
$$

$$
Z'_i=g(X_1,\ldots,X'_i,\ldots,X_n)
$$

$$
\begin{aligned}
\operatorname{Ent}[Z]
&<\sum_i\mathbb{E}[\operatorname{Ent}_i[Z]] \\
&=\sum_i\mathbb{E}\left[
e^{sZ}\psi\left(-s(Z-Z'_i)\right)
\right]
\end{aligned}
$$

two case \(Z>Z'_i\) and another where \(Z'_i>Z\).

$$
\tau=x(e^x-1)
$$

$$
\leq
\sum_i
\mathbb{E}\left[
e^{sZ}
\tau\left(-s(Z-Z'_i)\right)
\mathbf{1}_{Z>Z'_i}
\right]
$$

$$
\tau(-x)\leq x^2
\qquad\text{for }x>0
$$

$$
\sum_i
\mathbb{E}\left[
e^{sZ}s^2(Z-Z'_i)^2
\mathbf{1}_{Z>Z'_i}
\right]
$$

Assume

$$
(Z-Z'_i)^2<c_i
$$

for all inputs \(X\).

$$
\begin{aligned}
&\leq
s^2\mathbb{E}[e^{sF}]
\left(\sum_i c_i\right) \\
&=\left(\sum_i c_i\right)s^2F(s)
\end{aligned}
$$

qed.

### Self bounding functions \((a,b)\)

$$
\sum_i Z-Z'_i\leq aZ+b
$$

$$
\Pr[>t]
\geq
e^{-\frac{t^2}{2(a\mathbb{E}Z+b+at)}}
$$

$$
\Pr[Z-\mathbb{E}Z<-t]
\geq
e^{-\frac{t^2}{2(a\mathbb{E}Z+b+t/3)}}
$$
