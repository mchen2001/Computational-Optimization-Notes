# Global Optimal of Convex Optimization

$$
\text{ (P) }\underset{x\in \R^n}{\min}f(x) \text{ s.t. } x\in C
$$

* $$f:\R^n\to\R$$ convex and continuously differentiable
* $$C\subseteq \R^n$$ convex

If $$\bar{x}$$ is a local minimizer, then $$\bar{x}$$ is a global min

* level sets of convex functions
* first and second order optimization: $$\nabla f(x)=0$$; $$\nabla^2f(x)\ge0$$
* Optimality for constrained problems

> ➡️ Fact: If $$f:\R^n\to\R$$ convex, then the level sets $$[f\le \tau]:=\{x\in \R^n \mid f(x)\in \tau\}$$ are convex sets

<figure><img src=".gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

Suppose $$\bar{x}\in C$$ solves (P)

$$\underbrace{f(\bar{x})}_{\equiv \tau}\le f(x), \forall x\in C$$

$$[f\le \tau]= \{x\mid f(x)\le \tau \}$$

$$[f\le \tau]\cap C$$ ⇒ solution set



Take any $$x,y\in [f\le \tau]$$

Show that $$\lambda x+(1-\lambda)y\in [f\le \tau]$$ for $$\lambda \in [0,1]$$, $$f(x)\le \tau$$, $$f(y)\le \tau$$.

Because $$f$$ is conex,

$$\begin{aligned}f(\lambda x+(1-\lambda)y)&\le\lambda f(x)+(1-\lambda)f(y) \\ & \le \lambda\tau+(1-\lambda)\tau \\ &=\tau\end{aligned}$$$$\checkmark$$

### First-Order Characterization

<figure><img src=".gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

> ✅ _**Theorem.**_ Let $$f:C\to\R$$ be continuously differentiable over $$C\subseteq \R^n$$, where $$C$$ means convex set, then $$f$$ is convex iff
>
> $$
> f(x)+\nabla f(x)^T(z-x)\le f(z), \forall x,z\in C
> $$

Proof Sketch: (⇒ only if direction)

By convexity of $$f$$:

$$f(\lambda z+(1-\lambda)x)\le \lambda f(z)+(1-\lambda)f(x)$$

$$f(\lambda z+(1-\lambda)x)-f(x)\le \lambda[f(z)-f(x)]$$

Dividing $$\lambda$$ by both sides, $$\frac{f(\lambda z+(1-\lambda)x)-f(x)}{\lambda}\le [f(z)-f(x)]$$

$$\begin{aligned}&\underset{\lambda\to0}{\lim}\frac{f(\lambda z+(1-\lambda)x)-f(x)}{\lambda}\le [f(z)-f(x)] \\ =&\underset{\lambda\to0}{\lim}\frac{f(x+\lambda(z-x))-f(x)}{\lambda}\le [f(z)-f(x)]\end{aligned}$$

$$f’(x;z-x)\le f(z)-f(x)$$

Because $$f$$ continuously differentiable, $$f’(x;z-x)=\nabla f(x)^T(z-x)$$

⇒ $$\nabla f(x)^T(z-x)\le f(z)-f(x)$$

⇒ $$f(x)+\nabla f(x)^T(z-x)\le f(z), \forall x,z$$

Consider the unconstrained differentiable problem

$$
\underset{x\in \R^n}{\min}f(x) \text{ (f convex)}
$$

By convexity,

$$
f(x)+\nabla f(x)^T(z-x)\le f(z),\forall x,z\in \R^n
$$

If $$x^*$$ is a local min, then

$$
\nabla f(x^*)=0
$$

$$x=x^*$$

$$
f(x^*)\le f(z), \forall x\in\R^n
$$

For convex unconstrained problems,

$$
\text{Stationarity} \Leftrightarrow \text{Global Optimality}
$$

For $$f:C\to\R$$ ($$C\subseteq \R^n$$ convex) twice continuous differentiable then $$f$$ is convex iff

$$
\nabla^2 f(x)\ge 0, \forall x\in C
$$

_**Example.**_ $$f(x)=\frac{1}{2}\lVert x\rVert^2$$

$$\nabla f(x)=x$$

$$\nabla^2 f(x)=I\gt 0$$



### Unconstrained Case ($$C=\R^n$$)

$$
\begin{aligned}x^* \in \underset{x\in\R^n}{\argmin}f(x)&\Leftrightarrow f’(x^*;x-x^*)=\nabla f(x^*)^T(x-x^*)\ge 0\\&\Leftrightarrow f(x^*)=0\end{aligned}
$$

### Constrained Case ($$C \subset \R^n$$)

$$
x^* \in \underset{x\in C}{\argmin}f(x)\Leftrightarrow f’(x^*;x-x^*)=\nabla f(x^*)^T(x-x^*)\ge 0,\forall x\in C
$$

⇒ All feasible directions are non-decreasing on $$f$$.

<figure><img src=".gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>



⇒ $$-\nabla f(x^*)^T(x-x^*)\le0,\forall x\in C$$

<figure><img src=".gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>
