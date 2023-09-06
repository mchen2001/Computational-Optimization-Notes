# Optimality for Convex Optimization

$$
\underset{x\in \R^n}{\min} f(x) \text{ subject to } x\in C\subseteq \R^n
$$

* $$f:\R^n\to \R$$ continuous differentiable and convex
* $$C\subseteq \R^n$$ convex

### Unconstrained ($$C\subseteq \R^n$$)

### $$\begin{aligned}x^* \in \underset{x\in \R^n}{\argmin} &\Leftrightarrow \begin{aligned}0&\le f’(x^*;x-x^*), \forall x\in\R^n \\ &=\nabla f(x^*)^T(x-x^*)\end{aligned} \\ &\Leftrightarrow \nabla f(x^*)=0\end{aligned}$$



### Constrained ($$C\subseteq \R^n$$)

$$
x^* \in \underset{x\in C}{\argmin}f(x) \Leftrightarrow \begin{aligned}0 &\le f’(x^*;x-x^*),\forall x\in C\\&=\nabla f(x^*)^T(x-x^*),\forall x\in C\end{aligned}
$$

directional derivative is non-negative in all feasible directions

$$
-\nabla f(x^*)\in N_{\R_+^2}(x^*)\Leftrightarrow -\nabla f(x^*)^T(x-x^*)\le 0,\forall x\in C
$$

<figure><img src=".gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

### Normal Cone of a set $$C\subseteq \R^n$$ of a point $$x\in C$$

$$
N_C(x)=\{g\in \R^n \mid g^T(z-x)\le 0, \forall z\in C\}
$$

<figure><img src=".gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

_**Example.**_ $$C= \{x\in \R^n \mid Ax=b \}$$

$$
\begin{aligned}N_C(x)&=\left\{g\in \R^n \mid g^T(z-x)\le 0, \forall z\in C\right\}\\&=\left\{g\in\R^n\mid g^Td \le0,\forall d\in null(A)\right\}\\&=\left\{g\in \R^n \mid g^Td=0,\forall d\in null(A)\right\}\\&=null(A)^{\perp}\\&=range(A^T)\end{aligned}
$$

![](<.gitbook/assets/image (20).png>)

if $$z\in C$$, and $$x\in C$$

$$Ax=b$$

$$Az=b$$

$$A(z-x)=Az-Ax=b-b=0$$



$$range(A) \oplus null(A^T)=\R^m$$

$$range(A^T)\oplus null(A)=\R^n$$

### Linearly Constrained Optimization

$$
\underset{x\in\R^n}{\min}f(x)\text{ subject to } Ax=b \Leftrightarrow x\in C
$$

$$x^*$$ is a minimizer only if

$$\left \{ \begin{aligned}&\nabla f(x^*)=A^Ty\text{ for some } y\in\R^m \\ &Ax^*=b\end{aligned}\right.$$, where $$A$$ is a $$m\times n$$ matrix.

### New Lagrange of Normal Cones

$$\begin{aligned}&-\nabla f(x^*)\in N_C(x^*), x^*\in C \\ \Leftrightarrow & -\nabla f(x^*)\in range(A^T),Ax^*=b \\ \Leftrightarrow & \exist y^* \text{ s.t. } -\nabla f(x^*)=A^Ty\end{aligned}$$
