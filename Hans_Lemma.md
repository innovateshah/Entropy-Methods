# Han's Lemma

It's a statement about relative entropy used to derive the tensorization of entropy step.

Han's Lemma: Let \(X_1,\ldots,X_n\) be discrete random variables with finite joint entropy. For a subset \(S\subseteq[n]=\{1,\ldots,n\}\), write
\[
X_S := (X_i)_{i\in S}.
\]

Then, for every \(k\in\{1,\ldots,n\}\),

\[
\boxed{
\frac{1}{\binom{n}{k}}
\sum_{\substack{S\subseteq[n]\\|S|=k}}
H(X_S)
\geq
\frac{k}{n}H(X_1,\ldots,X_n)
}
\]

Equivalently,

\[
\boxed{
H(X_1,\ldots,X_n)
\leq
\frac{1}{\binom{n-1}{k-1}}
\sum_{\substack{S\subseteq[n]\\|S|=k}}
H(X_S).
}
\]

Here \(H(X_S)\) denotes the Shannon entropy of the joint random
