# Convex Functions

* definition
* relationship to convex sets
* operations preserve convexity
* global optimality (necessary $$\equiv$$ sufficient)

![](<.gitbook/assets/image (49).png>)

### Simplex

$$
\Delta_n = \{x\in \R^n \mid \sum x_i\le1, x\ge0\}
$$

### ![](<.gitbook/assets/image (50).png>)

### “Probability” Simplex

$$
\bar{\Delta}_n=\{x\in\R^n\mid\sum x_j=1, x\ge0\}
$$

$$\text{Conv}(S)= \{\sum_{i=1}^k\lambda_ix_i\mid\lambda \in\bar{\Delta}_k,x_i\in S,k\in \N \}$$, where $$\N$$ denotes non-negative

$$
\Delta_2=H^-_{\begin{pmatrix}0\\-1\end{pmatrix},0}\cap H^-_{\begin{pmatrix}-1\\0\end{pmatrix},0}\cap H^-_{\begin{pmatrix}1\\1\end{pmatrix},1}
$$

[Caratheodory’s Theorem](https://en.wikipedia.org/wiki/Carath%C3%A9odory's\_theorem\_\(convex\_hull\)) (Chp6, Beck)



Hyperplane: $$H_{a,\beta}= \{x\in \R^n\mid a^Tx=\beta \}$$

Halfspace: $$H^{-1}_{a,\beta}$$

$$
H^-_{a,\beta}=\{x\in\R^n\mid a^Tx\le\beta\}, (a\ne 0)
$$

![](<.gitbook/assets/image (51).png>)



_**Definition.**_ A function $$f:C\to \R$$, $$C\subseteq \R^n$$ (convex set), is _convex_ if

$$
f(\lambda x+(1-\lambda)y)\le\lambda f(x)+(1-\lambda)f(y)
$$

for any $$x,y\in C$$, and $$\lambda\in [0,1]$$



→ Difference between strict convex and convex?

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

_**Definition.**_ $$f$$ is concave if $$-f$$ is convex

_Consequence_: A function $$f$$ is concave and convex if and only if $$f$$ is affine

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

_Example_: Norm $$\lVert \cdot \rVert: \R^n\to\R_+$$

All norms satisfy the

1.  $$\Delta\text{-inequality}$$&#x20;

    $$
    \lVert x+y\rVert\le \lVert x\rVert+\lVert y\rVert
    $$
2. $$\lVert \alpha x\rVert=\lvert \alpha\rvert \cdot\lVert x\rVert$$



Take any $$x,y\in \R^n$$ and any $$\lambda \in [0,1]$$

$$
Z:=\lambda x+(1-\lambda)y
$$

$$\begin{aligned}\lVert Z\rVert &= \lVert \lambda x+(1-\lambda)y\rVert \\ &\le \lVert \lambda x\rVert+\lVert (1-\lambda)y\rVert \\ &=\lvert \lambda\rvert \cdot\lVert x\rVert+\lvert 1-\lambda\lvert\cdot \lVert y\rVert \\ &=\lambda\lVert x\rVert+(1-\lambda)\lVert y\rVert\end{aligned}$$



_**Example**_: Affine functions

$$
f(x)=a^Tx+\beta
$$

Ex: $$f(x)=-log(x), f:\R\to\R$$

![](<.gitbook/assets/image (12).png>)

Ex: $$f(x)=e^x f:\R\to\R$$

![](<.gitbook/assets/image (13).png>)

### Operations that preserve the convexity of functions

1.  **Non-negative multiples**

    $$\alpha f(x)$$ is convex if $$f(x)$$ is convex and $$\alpha \ge 0$$
2.  **Sums**

    $$f_1+f_2+\ldots+f_m$$ is convex if $$f_1,\ldots,f_m$$ are convex
3.  **Composition** of a convex function with affine function is convex, i.e.,

    if $$f$$ convex then $$f(Ax+b)$$ convex for _**any**_ matrix $$A$$ and vector $$b$$



    Proof:

    Take any point $$x,y\in \R^n$$ and $$\lambda \in [0,1]$$:

    $$f(A(\lambda x+(1-\lambda)y)+b)=f(\lambda(Ax+b)+(1-\lambda)(Ay+b))\le \lambda f(Ax+b)+(1-\lambda)f(Ay+b)$$



    _Example_ $$f(x_1,x_2,x_3)=e^{x_1-x_2+x_3}+e^{2x_2}+x_1$$

    _Example_ For any matrix $$A$$ and vector $$b$$, LS objective: $$\frac{1}{2}\lVert Ax-b\rVert_2^2$$

    $$\frac{1}{2}\lVert Ax-b\rVert_2^2=\frac{1}{2}\sum(a_i^Tx-b_i)^2=\frac{1}{2}\sum f(a_i^Tx-b_i)$$, where $$f(\cdot)=(\cdot)^2$$

### GLOBAL Optimality

(P) $$\underset{x\in\R^n}{\min}f(x)$$ subject to $$x\in C$$

where $$f:\R^n\to\R$$ convex and $$C\subseteq \R^n$$ convex set

If $$x^*$$ _is a local minimizer of (P), i.e.,_ $$f(x^*)\le f(x), \forall x\in \mathbb{B}_{\varepsilon}\cap C$$ for all $$\varepsilon \gt 0$$ small enough, then $$x^*$$ is a global minimizer of (P), _i.e._, $$f(x^*)\le f(x), \forall x\in C$$.



**Proof** Suppose $$x^* \in C$$ is a local minimizer of (P), but not a global minimizer.

$$\exists y\in C$$ s.t. $$f(y)\lt f(x^*)$$

By convexity of $$C$$, $$\lambda x^* +(1-\lambda)y\in C$$ for any $$\lambda \in [0,1]$$ and by convexity of $$f$$;

$$\begin{aligned} f(\lambda x^*+(1-\lambda)y)&\le \lambda f(x^*)+(1-\lambda)f(y) \\ &\lt \lambda f(x^*)+(1-\lambda)f(x^*) \\ &=f(x^*)\end{aligned}$$
