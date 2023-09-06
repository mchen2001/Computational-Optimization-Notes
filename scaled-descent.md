# Scaled Descent

* Scaled Descent
* Gauss-Newton Method
* Newton’s Method
* Diagonal Scaling

### Computing descend direction

$$x_0$$ given; $$\varepsilon > 0$$ convergence tolerance

for $$k = 0,1,2,…$$

* choose $$d_k$$ such that $$f(x_k+\alpha d_k)< f(x_k)$$ for some small $$\alpha > 0$$ (descent direction)
* line search: choose $$\alpha_k$$ for some small $$\alpha > 0$$ to enforce (descent)
* $$x_{k+1}=x_k+\alpha_k d_k$$
* check convergence: Exit if $$\lVert \nabla f(x_{k+1})\rVert < \varepsilon \cdot \lVert \nabla f(x_k)\rVert$$, e.g., $$\varepsilon=10^{-6}$$

### Scaled Descent

$$(P)$$$$\min_{x \in \mathbb{R}^n} f(x)$$ $$f:\mathbb{R}^n \to \mathbb{R}$$ continuous differentiable

Make a change of variables:

$$x:=Sy$$ or $$y=S^{-1}x$$

where $$S$$ is _**non-singular**_ and _**squares**_

**Ex:**

$$\begin{bmatrix} s_1 & & & &\\ &s_2&&&\\ & &s_3&& \\ & & & \ddots & \\ &&&&s_n \end{bmatrix}$$

$$Sw=0$$ iff $$w=0$$

$$S^Tv = 0$$ iff $$v=0$$

$$x=\begin{bmatrix}s_1 & & \\ & \ddots & \\&&s_n\end{bmatrix}\begin{bmatrix}y_1 \\ \vdots \\ y_n\end{bmatrix}$$⇒ $$x_i=s_iy_i$$

$$(P_{scaled})$$ $$\min_{y\in \mathbb{R}^n} g(y):=f(Sy)$$

Apply gradient descent to $$(P_{scaled})$$:

$$y_{k+1}=y_k-\alpha_k \nabla g(y_k)=y_k-\alpha_kS^T\nabla f(Sy_k)$$

$$\nabla g(y) = \nabla_y f(Sy) = S^T\nabla f(Sy)$$

application of chain rule and $$\nabla_x (a^Tx)=a$$

“Move” to the “x-space” by pre-multiple by $$S$$:

$$Sy_{k+1}=Sy_k-\alpha_kSS^T\nabla f(Sy_k)$$

$$x_{k+1}=x_k-\alpha_kSS^T\nabla f(x_k)$$

let $$D:=SS^T$$

$$D\nabla f(x)$$ is the “scaled” gradient of $$x$$

Is $$d = -D\nabla f(x)$$ a descent direction?

$$\begin{aligned}0> \nabla f(x)^Td & =\nabla f(x)^T(-D\nabla f(x)) \\ &= -\nabla f(x)^TD\nabla f(x) \\ &=-\nabla f(x)SS^T\nabla f(x) \\ &= -(S^T\nabla f(x))^T(S^T \nabla f(x))\\ &=-\lVert S^T\nabla f(x)\rVert^2\end{aligned}$$

If $$S$$ orthogonal ⇒ $$SS^T=I$$

Scaled descent ↔ unscaled descent

$$-D\nabla f(x)$$ descent direction if $$\nabla f(x)\ne 0$$ (i.e., not stationary)

![](<.gitbook/assets/image (32).png>)![](<.gitbook/assets/image (33).png>)

“Perfect” quadratic function:

$$f(x)=\frac{1}{2}x^Tx=\frac{1}{2}\lVert x\rVert^2$$

$$\nabla f(x)=x$$

$$\nabla_2 f(x)=I$$

$$\lambda_i(I)=1$$

$$cond(A)=\frac{\lambda_{max}(A)}{\lambda_{min}(A)}\ge 1$$

$$g(y)=f(Sy)$$

$$\nabla g(y)=S^T\nabla f(Sy)$$

$$\nabla^2g(y)=S^T\nabla^2f(Sy)\cdot S$$

where $$\nabla^2g(y)$$ is Hessian Symmetric ⇒ $$n\times n$$

⇒ choose $$S$$ to make $$\nabla^2 g(y)=S^T\nabla^2f(x)S$$ be “well-condition”, i.e., all eigenvalues are approximately the same

### Newton’s Method

Choose $$S$$ as $$S=(\nabla^2f(x))^{-\frac{1}{2}}$$

⇒

$$\begin{aligned}SS^T &=\nabla^2 f(x)^{-\frac{1}{2}}(\nabla^2 f(x)^{-\frac{1}{2}})^T \\ &=\nabla^2 f(x)^{-\frac{1}{2}} \cdot \nabla^2 f(x)^{-\frac{1}{2}} \\ &= \nabla^2 f(x)^{-1}\end{aligned}$$

If $$\nabla^2 f(x)$$ is pos-def, then $$\nabla^2 f(x)=D^{-\frac{1}{2}}\cdot D^{-\frac{1}{2}}$$ for some $$D$$ non-singular

$$\begin{aligned}\nabla^2 g(y)=S^T\nabla^2f(x)S &= \nabla^2 f(x)^{-\frac{1}{2}}\nabla^2 f(x)\nabla^2 f(x)^{-\frac{1}{2}} \\ &=\nabla^2 f(x)^{-\frac{1}{2}}(\nabla^2 f(x)^{\frac{1}{2}} \cdot \nabla^2 f(x)^{\frac{1}{2}})\nabla^2 f(x)^{-\frac{1}{2}}\\ &=I\end{aligned}$$

### Newton’s direction at $$x$$

$$\begin{aligned}d_N &= -SS^T\nabla f(x)\\ &=-\nabla^2f(x)^{-1}\cdot \nabla f(x)\end{aligned}$$

i.e., Newton direction $$d_N$$ is the solution of the pos-def system (linear)

Newton Equation: $$\nabla^2 f(x)\cdot d=-\nabla f(x)$$

### Newton’s Method Steps

$$x_0$$ given; $$\varepsilon > 0$$

for $$k = 0,1,2,…$$

* $$d_N$$ solves $$\nabla^2f(x_k)d=-\nabla f(x_k)$$
* line search on $$\alpha$$
* $$x_{k+1}=x_k+\alpha_k d_k$$
* check convergence, $$\lVert \nabla f(x_k)\rVert$$ small

work $$O(n^3)$$

$$\begin{aligned}\nabla^2 f(x) & = U \Lambda U^T \text{ eigen decompose} \\ &=(U\Lambda^{\frac{1}{2}})(U\Lambda^{\frac{1}{2}})^T\end{aligned}$$

Set $$S=(U\Lambda^{\frac{1}{2}})^{-T}=(\Lambda^{-\frac{1}{2}}U^{-1})^T=U^{-T}\Lambda^{-\frac{1}{2}}=U\Lambda^{-\frac{1}{2}}$$

$$\begin{aligned} \nabla^2 g(y) &= S^T\nabla^2 f(x)S\\ &= (\Lambda^{-\frac{1}{2}}U^T)(U\Lambda U^T)(U\Lambda^{-\frac{1}{2}})\\ &= \Lambda^{-\frac{1}{2}}\cdot \Lambda \cdot \Lambda^{-\frac{1}{2}} \\ &=I\end{aligned}$$

### Gauss-Newton

$$\min_{x\in \mathbb{R}^n} f(x):=\frac{1}{2}\lVert r(x)\rVert^2$$

$$r(x)=\begin{bmatrix}r_1(x)\\ \vdots \\ r_m(x)\end{bmatrix}$$, where $$r_i: \mathbb{R}^n \to \mathbb{R}$$

$$\nabla f(x) = J(x)r(x)$$



**G-N iteration:**

$$\begin{aligned}x_{k+1} &=\argmin_x \frac{1}{2}\lVert \underbrace{r(x_k)+J(x_k)^T(x-x_k)}_{\text{linearization of r at }x_k}\rVert^2\\ &= \argmin_x \frac{1}{2} \lVert J_k^Tx-(J_k^Tx_k-r_k)\rVert^2\\ &=(J_kJ_k^T)^{-1}J_k(J_k^Tx_k-r_k)\\ &=x_k-(J_kJ_k^T)^{-1}J_kr_k\\ &=x_k-(J_kJ_k^T)^{-1}\nabla f(x_k)\end{aligned}$$

(normal equation: $$\frac{1}{2}\lVert Ax-b\rVert^2$$⇒$$x=(A^TA)^{-1}A^Tb$$)
