# Regularization

### Motivation:

We wish to choose $$x$$ to balance the two objective values

$$f_1(x)=\lVert Ax-b\rVert^2$$ and $$f_2(x)=\lVert Cx-d\rVert^2$$.

Generally, we can make $$f_1(x)$$ or $$f_2(x)$$ small, but not both.

b is observation (noisy)

Naive Least-Sq formation:

true signal $$x_0$$ recovered via $$\underset{x}{\min} \lVert x-b\rVert^2$$

$$b=x_0+noise$$ ⇒ $$x_0-b=noise$$

Need to incorporate “side” information

“side” ↔ ”prior” ⇒ signal $$x_0$$ is smooth

Combining two models

$$\underset{x}{\min}f_1(x)+f_2(x)$$

Balance competing objectives $$f_1$$ and $$f_2$$

1.  $$\underset{x}{\min}\{f_1(x)+\lambda f_2(x)\}$$, $$\lambda ≥ 0$$

    $$\lambda$$: “regularization” parameter

    $$f_2(x)$$: regularization function
2.  $$\underset{x}{\min}\{f_1(x)\mid f_2(x)≤\tau\}$$, $$\tau ≥ 0$$ $$\min\{f_1(x) \mid \forall x \text{ st. } f_2(x) \le \tau\}$$&#x20;

    $$\min\{f_1(x)\mid x \in lev_\tau f_2\}$$
3. $$\min\{f_2(x)\mid f_1(x)≤ \Delta\}$$, $$\Delta≥ 0$$

### **Tikhonov regularization**

A particularly common example of regularized least-squares is [Tikhonov](https://en.wikipedia.org/wiki/Tikhonov\_regularization), which has the form

$$
\underset{x}{\min}\frac{1}{2}\lVert Ax-b\rVert^2+\lambda \frac{1}{2}\lVert Dx\rVert^2
$$

for which the objective can be expressed as

$$
\lVert Ax-b\rVert^2+\lambda \lVert Dx\rVert^2=\lVert \begin{bmatrix}A\\ \sqrt{\lambda}D\end{bmatrix}x-\begin{bmatrix}b\\ 0\end{bmatrix}\rVert^2
$$

If $$D$$ has full column rank, then the stacked matrix

$$
\begin{bmatrix}A\\\sqrt{\lambda}D\end{bmatrix}
$$

necessarily also has full rank for any positive $$\lambda$$, which implies that the regularized problem always has a well-defined unique solution.



💡 _**Example.**_

$$\min\{f_2(x)\mid \lVert x-b\rVert^2≤\Delta\}$$&#x20;

Choose $$f_2$$ that promotes “smoothness”&#x20;

signal $$x=(x_1,x_2,x_3,…,x_n)$$



Measure smoothness by measuring change between $$x_{i+1}$$ and $$x_i$$: $$f_2(x)=\sum^{n-1}{i=1}(x_i-x{i+1})^2$$

$$
\underset{x}{\min}\frac{1}{2}\underbrace{\lVert x-b\rVert^2}_{f_1(x)}+\lambda \frac{1}{2} \underbrace{\sum^{n-1}_{i=1}(x_i-x_{i+1})^2}_{f_2(x)}.
$$

Matrix notation:

$$D = \begin{bmatrix} 1 & -1 & 0 & \ldots & \ldots & 0\\ 0 & 1 & -1 & 0 & \ldots & 0\\ 0 & 0 & 1 & -1 & \ldots & 0\\ & &\ddots \\ 0 & 0 & \ldots & 0 & 1 & -1\end{bmatrix}$$

$$f_2(x)=\lVert Dx\rVert^2$$

$$Dx = \begin{bmatrix} x_1-x_2\\ x_2-x_3\\ \vdots \\ x_{n-1}-x_n \end{bmatrix}$$&#x20;

This allows for a reformulation of the weighted least squares objective into a familiar least squares objective:

$$
\lVert x-b\rVert^2+\lambda \lVert Dx\rVert^2=\lVert \underbrace{\begin{bmatrix}I\\\sqrt{\lambda}D\end{bmatrix}}_{\hat{A}}x-\underbrace{\begin{bmatrix}b\\ 0\end{bmatrix}}_{\hat{b}}\rVert^2
$$

So the solution to the weighted least squares minimization program satisfies the normal equation $$\hat{A}^T\hat{A}x=\hat{A}^T\hat{b}$$, which simplifies to

$$
(I+\lambda D^TD)x=b.
$$
