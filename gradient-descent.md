# Gradient Descent

solves $$\min \frac{1}{2} \lVert Ax-b\rVert^2$$

check if $$x^*$$ _solves_ as $$A^TAx^*=A^Tb$$

$$A^T(Ax^*-b)=0$$

$$\lVert A^Tr^*\rVert\le \varepsilon$$

$$\underset{x\in \mathbb{R}^n}{\min}f(x)$$, $$f:\mathbb{R}^n \to \mathbb{R}$$ smooth

(later: $$x\in C \le \mathbb{R}^n$$)

### Optimality

$$\bar{x}$$ is a …

1.  local min of $$f$$ if $$f(\bar{x}) \le f(x), \forall x \in B_\varepsilon(\bar{x})$$, for some $$\varepsilon>0$$ small,

    where $$B_\varepsilon(\bar{x})={x \mid \lVert x-\bar{x}\rVert_2 \le \varepsilon}$$
2. global min of $$f$$ if $$f(\bar{x})≤f(x), \forall x \in \mathbb{R}^n$$

$$\bar{x}$$ is a maximizer of $$f$$ ↔ $$\bar{x}$$ is a minimizer of $$-f$$

![](<.gitbook/assets/image (25).png>)![](<.gitbook/assets/image (26).png>)

**Ex**: lack of attainment

$$\underset{x \to \infty}{\lim} e^{-x}=0$$

$$\underset{x}{\inf}e^{-x}=0$$

$$e^{-x}$$ is not coercive

![](<.gitbook/assets/image (27).png>)![](<.gitbook/assets/image (28).png>)

**Definition**: A function f is coercive if $$\underset{\lVert x\rVert \to \infty}{\lim} f(x) = \infty$$

Equivalently The level sets $$\{x \mid f(x) \le \tau\}$$ for any $$\tau \in \mathbb{R}$$ are all compact (closer & bond)

### First-order necessary condition

$$\bar{x}$$ is a local min of $$f:\mathbb{R}^n \to \mathbb{R}$$ **only if** $$\nabla f(\bar{x})=0$$

$$\left [ \overset{\bar{x}}{\text{local min}} \to \nabla f(\bar{x})=0 \right ]$$

$$\left [ \overset{\bar{x}}{\text{local max}} \to \nabla f(\bar{x})=0 \right ]$$

$$[\ \overset{\bar{x}}{\text{local max}} \to \nabla f(\bar{x})=0 ]\$$

**Proof sketch**: Up to first-order

$$f(\bar{x}+\alpha d)-f(\bar{x})=\nabla f(\bar{x})^T(\alpha d)+o(\alpha \lVert d\rVert)$$

Because $$\bar{x}$$ is a local min,

$$o\le \underset{\alpha \to 0}{\lim}\frac{f(\bar{x}+\alpha d)-f(\bar{x})}{\alpha}=\underset{\alpha \to 0}{\lim}\nabla f(\bar{x})^Td+\frac{o(\alpha \lVert d\rVert)}{\alpha}=\nabla f(\bar{x})^Td$$

→ $$\nabla f(\bar{x})=0$$

### 2nd-order sufficient condition

$$\bar{x}$$ is a local min of $$f:\mathbb{R}^n \to \mathbb{R}$$ if

* $$\nabla f(\bar{x})=0$$ (stationary)
* $$\nabla^2 f(\bar{x})\gt 0$$ (positive definite of Hessian)

$$[\ \nabla f(\bar{x})=0$$ $$&$$ $$\nabla^2 f(\bar{x})\gt 0$$⇒ $$\bar{x}$$ local min $$]\$$

$$f’’(x_{global})\gt 0$$

$$f’’(x_{local})\gt 0$$

$$f’’(x’_{local})=0$$

$$f’’(x_{max})\lt 0$$

![](<.gitbook/assets/image (29).png>)

**Ex**: $$f(x)=x^4$$

$$f’(0)=0$$

$$f’’(0)=0$$



**Definition**: A matrix (square/symmetric) A is positive semi-definite (i.e., $$A \ge 0$$) if the following equivalent conditions hold:

1. $$x^TAx \ge 0, \forall x\in \mathbb{R}^n$$
2. $$\lambda_i(A) \ge 0, \forall i=1,…,n$$
3. $$A=R^TR, \exists R$$ (Cholesky factory exists)

**Positive Definite**

1. $$x^TAx \gt 0, \forall x \ne 0$$
2. $$\lambda_i(A) \gt 0, \forall i$$
3. $$A=R^TR$$, $$R$$ non-singular

**Proof Sketch**: Up to second-order:

$$f(\bar{x}+\alpha d)-f(\bar{x})=\alpha\underbrace{\nabla f(\bar{x})^T}_0d+\underbrace{\frac{1}{2}\alpha^2d^T\nabla^2 f(\bar{x})d} _{\gt 0}+o(\alpha^2\lVert d\rVert^2)$$

take $$\alpha$$ “small”

→ $$\bar{x}$$ is a local min

### 2nd-order necessary condition

$$\bar{x}$$ is a local min of $$f:\mathbb{R}^n \to \mathbb{R}$$ only if

* $$\nabla f(\bar{x})=0$$ (stationary)
* $$\nabla^2 f(\bar{x})\ge 0$$ (positive semi-definite)

Eigen pair $$(x,\lambda)$$ of $$A$$ sq. symm:

$$Ax=\lambda x$$

$$x^TAx=\lambda \underbrace{x^Tx}_1=\lambda$$

($$\lambda \gt 0$$ means the direction does not change)

Ex: $$\min \frac{1}{2}\lVert r(x)\rVert^2=\frac{1}{2}\sum^m_{i=1}r_i(x)^2$$, $$r_i:\mathbb{R}^n \to \mathbb{R}$$

$$f(x)=\frac{1}{2}\lVert r(x)\rVert^2=\frac{1}{2}r_1(x)^2+\frac{1}{2}r_2(x)^2+…$$

$$\begin{aligned}\nabla f(x) & =\nabla r_1(x)\cdot r_1(x)+\nabla r_2(x)\cdot r_2(x)+…\\ &= \begin{bmatrix}\mid & \mid & & \mid\\ \nabla r_1(x) & \nabla r_2(x) & \ldots & \nabla r_m(x)\\ \mid & \mid & & \mid\\ \end{bmatrix}\begin{bmatrix}r_1(x)\ r_2(x)\\ \vdots\\ r_m(x)\end{bmatrix}\\ &= J(x)^Tr(x)\end{aligned}$$

stop when $$\lVert J(x)^T r(x)\rVert=\lVert \nabla f(x)\rVert$$ small

### Least-Square (Linear)

$$f(x)=\frac{1}{2}\lVert Ax-b\rVert^2=\frac{1}{2}\lVert r(x)\rVert^2$$

where $$r_i(x)=a_i^Tx-b_i, \nabla r_i(x)=a_i$$

$$\begin{aligned}\nabla f(x) & =\begin{bmatrix}\mid & \mid & & \mid\\ a_1 & a_2 & \ldots & a_m\\ \mid & \mid & & \mid \end{bmatrix}\begin{bmatrix}a_1^Tx-b_1\\ a_2^Tx-b_2\\ \vdots\\ a_m^Tx-b_m\end{bmatrix}\\ &= A^T(Ax-b)\end{aligned}$$,

where $$A=\begin{bmatrix}-a^T_1-\\-a^T_2-\\ \vdots \\ -a^T_m-\end{bmatrix}$$ and $$a_i$$ is $$n \times 1$$ vector.

$$\nabla f(x)=0$$ ↔ $$A^TAx=A^Tb$$

### Gradient Descent

* step size selection (linearized)
* search direction selection

$$\underset{x \in \mathbb{R}^n}{\min} f(x)$$ $$f:\mathbb{R}^n \to \mathbb{R}$$ continuously differentiable

### Descent Direction

$$x^0$$ given

for $$k = 0,1,2,…$$

$$x^{k+1}=x^k+\alpha^kd^k$$

* $$d^{k \in \mathbb{R}^n}$$ search direction
* $$\alpha^k \in \mathbb{R}_+$$ step length

“Linesearch Methods”

<figure><img src=".gitbook/assets/image (30).png" alt=""><figcaption><p>A search direction <span class="math">d \in \mathbb{R}^n</span> is a descent direction at x if the directional derivative is negative: <span class="math">\nabla f(x)^Td=f’(x;d) \lt 0</span></p></figcaption></figure>



if $$f: \mathbb{R}^n \to \mathbb{R}$$ is continuous differentiable and $$d \in \mathbb{R}^n$$ is a descent direction, then $$\exist$$ some $$\varepsilon \gt 0$$ such that $$f(x+\alpha d) \lt f(x), \forall \alpha \in (0,\varepsilon]\$$

Proof Sketch

* because $$f’(x;d) \lt 0$$, $$\underset{\alpha \to 0}{\lim}\frac{f(x+\alpha d)-f(x)}{\alpha} \equiv f’(x;d) \lt 0$$
* because $$f$$ is continuous, $$\exist$$ small $$\alpha$$ such that $$f(x+\alpha d) \lt f(x)$$

### Conceptual Algorithm

$$x^0$$ given for $$k=0,1,2,…$$

* compute search direction $$d^k$$ (given $$x^k$$)
* compute step size $$\alpha_k$$ such that $$f(x^k+\alpha^kd^k)\lt f(x^k)$$
* update $$x^{k+1}=x^k+\alpha^kd^k$$
* check stop criteria

### Step Size Selection ($$\alpha^k$$)

1. constant step $$\alpha^k \equiv \alpha$$ ($$\alpha \gt 0, \forall k$$)
2.  exact linesearch (not always possible)

    choose $$\alpha^k$$ such that

    $$\underset{\alpha \ge 0}{\min} \phi (\alpha) := f(x^k+\alpha d^k)$$
3.  backtracking linesearch (”Aruijo”)

    reduce $$\alpha$$ in steps (eg $$\alpha ← \alpha/2$$ until $$f(x^k+\alpha d^k) \lt f(x^k)$$



**Exact Linearization**

* not always possible
*   always possible for quadratic functions

    $$f(x)=\frac{1}{2}x^TAx+b^Tx+const$$

    $$\begin{aligned} \phi(x) & = f(x+\alpha d) \\ & = \frac{1}{2}(x+\alpha d)^TA(x+\alpha d)+b^T(x+\alpha d)+const \\ & = \frac{1}{2}x^TAx+b^Tx+\frac{1}{2}\alpha^2d^TAd+\alpha b^Td+\alpha d^T Ax+ const\\ & = f(x)+\alpha^2 \frac{1}{2}d^TAd+\alpha\underbrace{(Ax+b)^T}_{\equiv \nabla f(x)^T}d+const \\ & = f(x)+\alpha^2\frac{1}{2}d^TAd+\alpha \nabla f(x)^Td+const \end{aligned}$$

At (unconstrained) minimizer of $$\phi$$, $$0=\phi’(\alpha)=\alpha d^T Ad+\nabla f(x)^T d ↔ \alpha =\frac{-\nabla f(x)^Td}{d^TAd}$$

1. d is descent direction ⇒ $$\nabla f(x)^Td \lt 0$$
2. if $$d^TAd \gt 0$$

if a & b ⇒ $$\alpha \gt 0$$

If $$A \gt 0$$ and d is a descent direction (i.e., $$\nabla f(x)^Td \lt 0$$)

⇒ $$\alpha = \frac{-\nabla f(x)^Td}{d^TAd} \gt 0$$

suppose $$\nabla f(x)^Td=0$$

### Choosing Search Direction d

![](<.gitbook/assets/image (31).png>)

steepest descent $$d^k=-\nabla f(x^k)\equiv \nabla f_k$$

Always provides descent direction:

$$\begin{aligned}f’(x^k;d^k) &= \nabla f(x^k)^Td^k\\ & = \nabla f(x^k)^T(-\nabla f(x^k)) \\ & = -\nabla f(x^k)^T \nabla f(x^k) \\ & = -\lVert \nabla f(x^k) \rVert^2 \end{aligned}$$

If $$\nabla f(x^k) \ne 0$$ (i.e., $$x^k$$ not stationary)

⇒

$$d^k = -\nabla f_k$$ descent direction

### “Steepest” Descent is “Greedy”

First-order Taylor approximation of f at $$x^k$$,

$$f(x+d) \approx f(x)+\nabla f(x)^Td ⇒ f(x+d)-f(d) \approx \nabla f(x)^Td$$

choose d to minimize $$f(x+d)-f(x)$$,

i.e., $$\underset{\lVert d \rVert_2 \le 1}{\min} \nabla f(x)^Td$$ ⇒ choose $$d = \frac{-\nabla f(x)}{\lVert \nabla f(x) \rVert}$$ (i.e., $$\lVert d \rVert_2 =1$$)

$$\begin{aligned} \nabla f(x)^Td &= -\nabla f(x)^T\frac{\nabla f(x)}{\lVert \nabla f(x) \rVert_2} \\ & = - \frac{\lVert \nabla f(x) \rVert_2^2}{\lVert \nabla f(x) \rVert_2} \\ & = - \lVert \nabla f(x) \rVert_2\end{aligned}$$

By Cauchy-Schwarz in e.g., $$-\lVert a \rVert_2 \cdot \lVert b \rVert_2 \le a^Tb \le \lVert a \rVert_2 \cdot -\lVert b \rVert_2, \forall a,b \in \mathbb{R}^n$$
