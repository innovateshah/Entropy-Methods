
We observe that the nice property of $A(x)=e^x$ is that A(x+y)=A(x)A(y).

A possible idea is to find other functions like e^x where $A(f(x_1,x_2...x_n))=F(A(x_1),A(x_2)...A(x_n), x_1, x_2... x_n)$ where $F$ is one nice function and f is what we actually care about bounding.

An example, let $A(x)=arctanh^{-1}(x)$, $f(x,y) = (x+y)/(xy+1)$ and $F=A(x)+A(y)$ Then
```math
Pr(A(f(x,y)) > A(k) ) < E[A(f(x,y))] / A(k) = (E[x]+E[y])/A(k).
```
This seems like a very nice identity that does not even require independence of our random variables. However this is purely theoretical.
It would be nice come up with some general framework that generates a suitable pair $A,F$ from our known $f$.
This seems unlikely.

It seems that trigonometric functions have extremely rich properties. Here is another example that is more apt for k-wise.
So A(x)=arcsinh(x),

```math

```


A generalized result involving inverses but first we let $x \in \mathbb{R}^n$, and if $S \subseteq [n]$ then we let $x_S$ be the tuple containing $x_i$ if $i \in S$.
We also fix $k<n$. We also let $A(x)$ be the function which we will use Chebyshev inequality with, and any invertible $h: R \mapsto [0,\infty)$


```math
e_k(x) = \sum_{S \subseteq [n],|S|=k} x_S \\
g(x_S) = \prod_{i \in S} h(x_i) \\
f(x) = A^{-1}(e_k(h(x_1), h(x_2)... h(x_n)) )
```

But going in the opposite direction (that is going from and f to a good A) is HARD. However it might be possible to find general upper bounds.
Regardless here is the "useful conclusion" if our input $X$ is k-wise independent, our main result is as follows

```math
E[A(f(x))] = e_k(E[h(x_1)], E[h(x_2)]... E[h(x_n)])
```

So our probability bound is

```math
Pr(f(x) > \lambda ) <= e_k(E[h(x_1)], E[h(x_2)]... E[h(x_n)]) / A(\lambda)
```



