# Linear Constraints

$$\underset{x \in \R^n}{\lim} f(x)$$ subject to $$\underbrace{Ax=b}_{\text{undetermined system}}$$

* effectively an “unconstrained problem”
* geometric introduction Lagrange Multipliers
* Connection to QR decomposition

Matrices $$A=m \times n$$, $$b=m \times 1$$

* $$m$$ constants; $$n$$ variables
* $$rank(A)=m$$ (full-rank)
  * $$f:\R^n \to \R$$ continuous differentiable once or twice
  *   Feasible Set

      * $$F=\{x \mid Ax=b\}=\phi \Leftrightarrow b\in Range(A)$$

      ![](<.gitbook/assets/image (38).png>)

### Equivalent representation of feasible set

$$F=\{x \mid Ax=b\}=\{\bar{x}+Zp \mid p \in \R^{n-m}\}$$,

$$\begin{aligned}\text{where } & \bar{x}\text{ is any “particular” solution for }A\bar{x}=b,\\ & Z \text{ is any basis for }Null(A) (Z \text{ is }n\times (n-m) \text{ s.t. }AZ=0),\\& p\text{ along the null basis}\end{aligned}$$

### ![](<.gitbook/assets/image (39).png>)

### Equivalent Reduced Problem

$$\underset{p \in \R^{n-m}}{\lim} f(\bar{x}+Zp) \equiv \underset{x \in \R^{n}}{\lim}{f(x)\mid Ax=b}$$

* $$\bar{x}+Zp^* \equiv x^*$$

**Example:**

$$
\lim \frac{1}{2}(x_1^2+x_2^2) \text{ s.t. } x_1+x_2=1
$$

eliminate e.g., $$x_2=1-x_1$$ substitute

$$\underset{x_1 \in \R}{\lim}\frac{1}{2}(x_1^2+(1-x_1)^2)$$

$$\begin{aligned}\text{set derivative = 0 ⇒}x_1-(1-x_1) &=0 \\ 2x_1-1 &= 0\\ x_1 &=\frac{1}{2} \end{aligned}$$

$$x_2 = \frac{1}{2} ⇒ (x_1,x_2)=(\frac{1}{2},\frac{1}{2})$$

![](<.gitbook/assets/image (40).png>)

### Optimality Conditions for “Reduced” Problem

$$
\underset{p \in \R^{n-m}}{\lim} f(\bar{x}+Zp) \equiv f_Z(p)
$$

1-st order necessary optimal condition $$\nabla_p f_Z(p)=0$$

$$0=\underbrace{\nabla_p f_Z(p)}_{(n-m)\times 1}=\underbrace{Z^T}_{(n-m)\times n}\underbrace{\nabla f(\bar{x}+Zp)}_{n\times1}$$

⇒ $$p^*$$ is a solution only if $$\nabla_p f_Z(p)=0 \Leftrightarrow Z^T\nabla f(\bar{x}+Zp^*)=0$$

let $$x^* := \bar{x}+Zp^*$$ implies

$$Z^T\nabla f(x^*)=0 \Leftrightarrow \nabla f(x^*) \in Null(Z^T)$$

**Four Fundamental Subspaces Associated with** $$A$$ **and** $$Z$$

$$range(A^T)\oplus Null(A)=\R^n$$

$$Null(Z^T)\oplus range(Z)=\R^n$$

$$\begin{aligned}\nabla f(x^*) \in Null(Z^T) &\Leftrightarrow \nabla f(x^*) \in range(A^T) \\ &\Leftrightarrow \exist y \in \R^m\text{ s.t. } \nabla f(x^*)=A^Ty\end{aligned}$$



### First-order Necessary Condition for

$$\underset{x\in \R^n}{\lim}{f(x)\mid Ax=y}$$(p)

*   A point $$x^*$$ is a local minimizer (stationary) of ($$p$$) only if there exists a vector $$y \in \R^m$$ s.t.:

    $$\left \{\begin{aligned}&\nabla f(x^)=A^Ty &, &\text{ optimality} \\ &Ax^=b&,&\text{ feasibility}\end{aligned}\right.$$

    \*Note: $$y$$ sometimes referred to as “_**Lagrange Multipliers**_”

### Lagrangian Function

$$
L(x,y)=f(x)-y^T(Ax-b)
$$

find a stationary pair $$(x,y)$$ of $$L$$:

$$0=\nabla_x L(x,y)=\nabla f(x)-A^Ty$$

$$0=\nabla_y L(x,y)=-(Ax-b)$$

\*\* $$\Leftrightarrow Z^T \nabla f(x^)=0 \Leftrightarrow \nabla f(x^*)^Tp=0, p\in Null(A)$$



**Example Least-Norm Solutions for Underdetermined**

**Linear-Systems**

$$\lim \lVert x\rVert_2$$ subject to $$Ax=b$$ (underdetermined)

Take $$f(x)=\frac{1}{2}\lVert x\rVert_2^2$$, $$\nabla f(x)=x$$

First-order optimality: $$(x,y)$$ satisfies

<figure><img src=".gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

$$X_{LS}=(A^TA)^{-1}A^Tb$$ (over-determined) normal equation

**Example: min-norm to** $$x_1+x_2+\cdots+x_n=1$$

$$m=1$$

$$x_1+x_2+\cdots+x_n=\underbrace{\begin{bmatrix}1&1&\cdots&1\end{bmatrix}}_A\underbrace{\begin{bmatrix}x_1 \\ x_2\\ \vdots \\ x_n\end{bmatrix}}_x=\underbrace{1}_b$$

$$A=e^T\equiv \begin{bmatrix}1&1&\cdots&1\end{bmatrix}$$

$$x=e(e^Te)^{-1}=e(w)^{-1}=\frac{1}{w}e=\begin{bmatrix}\frac{1}{w} \\ \vdots \\ \frac{1}{w}\end{bmatrix}$$

Second-order Necessary Conditions $$x^*$$ is a local minimizer only if

$$\left \{ \begin{aligned}\nabla^2 f_Z(x^)\ge 0 \\ Ax^=b\end{aligned}\right.$$
