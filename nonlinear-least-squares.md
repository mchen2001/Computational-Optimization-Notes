# Nonlinear Least-Squares

* general definition
* linearization
* Gauss-Newton

### Nonlinear LS:

$$\underset{x\in \mathbb{R}^n}{\min}\frac{1}{2}||r(x)||^2_2$$ , where

$$
r(x)=\begin{bmatrix}r_1(x) \\ r_2(x)\\ \vdots\\ r_m(x)\end{bmatrix}
$$

$$r_i(x):\mathbb{R}^n→\mathbb{R}$$

$$i=1 \ldots m$$

$$m$$ outputs, $$n$$ inputs



Special case: Linear Least-Square:

$$\begin{aligned}r(x)=\begin{bmatrix}r_1(x) \\ r_2(x)\\ \vdots \\ r_m(x)\end{bmatrix}& =\begin{bmatrix}b_1-a^T_1x \\ b_2-a^T_2x \\ \vdots \\ b_m-a^T_mx \end{bmatrix}=[\ b_i-a^T_ix]\ ^m_{i=1}\\ &=b-Ax\end{aligned}$$

where $$A=\begin{bmatrix}-a^T_1-\\-a^T_2-\\ \vdots \\ -a^T_n-\end{bmatrix}$$, and $$A$$ is $$m \times n$$.

$$m>n$$: overdetermined

$$m<n$$: underdetermined



More generally, nonlinear model:

$$r_i(x)=b_i-f_i(x)$$, $$f_i(x):\mathbb{R}^n→\mathbb{R}$$



_**Example**_**:** position estimation→ “sensor localization”

<img src=".gitbook/assets/image (6).png" alt="" data-size="original">

nonlinear LS form: to obtain position estimate

$$\underset{x\in \mathbb{R}^2}{\min}\sum_{i=1}^m(\lVert x-b_i\rVert_2-s_i)^2$$

$$m$$ beacons $$b_i \in \mathbb{R}^2$$, $$i=1 \ldots m$$



Nonlinear Least-Squares

$$\underset{x \in \mathbb{R}^n}{\min}\frac{1}{2}\lVert r(x) \rVert^2=\frac{1}{2}\sum_{i=1}^m r_i(x)^2$$

$$r(x)=\begin{bmatrix} r_1(x) \\ \vdots \\ r_m(x) \end{bmatrix}$$, $$r_i(x):\mathbb{R}^n→\mathbb{R}$$



Sensor localization example:

![](<.gitbook/assets/image (7).png>)

$$r(x)= \begin{bmatrix} \lVert x-b_1\rVert-f_1\\ \lVert x-b_2\rVert-f_2\\ \ \vdots \\ \lVert x-b_m\rVert-f_m\end{bmatrix}$$

residual $$r_i(x)=\lVert x-b_i \rVert_2-f_i$$

Special case:

$$r_i(x)=a_i^Tx-b_i$$

$$r(x)=Ax-b$$

$$\frac{1}{2}\lVert r(x)\rVert^2=\frac{1}{2}\lVert Ax-b\rVert^2$$: linear least squares

###

### Gauss-Newton

* start with some guess for solution $$x^{(0)}$$
* for $$k = 0,1,2,3,…$$
  * linearize the residuals $$r_i$$ at the current iterate $$x^{(k)}$$
    * $$\bar{r}^{(k)}(x)$$ ← linearization at $$x^{(k)}$$
  * $$x^{(k+1)}=\underset{x\in \mathbb{R}^n}{\argmin} \frac{1}{2} \lVert \bar{r}^{(k)}(x)\rVert^2$$
  *

Linearization of a generic $$f:\mathbb{R}^n\to \mathbb{R}$$ at a point $$x\in \mathbb{R}^n$$

![](<.gitbook/assets/image (23).png>)

$$f(x+d)=f(x)+\nabla f(x)^Td+o(\lVert d\rVert)$$

or equivalently: $$z=x+d$$ or $$d=z-x$$

$$f(z)=f(x)+\nabla f(x)^T(z-x)+o(\lVert z-x\rVert)$$

(little “oh”) $$g\in o(\varepsilon)$$ if $$\underset{\varepsilon → 0}{\lim}\frac{g(\varepsilon)}{\varepsilon}=0$$



**Sensor Localization Example**

$$r(x)= \begin{bmatrix} \lVert x-b_1\rVert-f_1\\ \lVert x-b_2\rVert-f_2 \\ \vdots \\ \lVert x-b_m\rVert-f_m\end{bmatrix}$$

linearization of vector-valued function $$r(x):\mathbb{R}^n→\mathbb{R}^n$$:

$$\begin{aligned}\bar{r}^{(k)}(x)& =\begin{bmatrix} r_1(x^{(k)})+\nabla r_1(x^{(k)})^T+o(\lVert x-x^k\rVert) \\ \vdots\ r_m(x^{(k)})+\nabla r_m(x^{(k)})^T+o(\lVert x-x^k\rVert)\end{bmatrix}\\ & =\begin{bmatrix}r_1(x^{(k)})\\ \vdots\\ r_m(x^{(k)})\end{bmatrix}+\begin{bmatrix}\nabla r_1(x^{(k)})^T\\ \vdots\\ \nabla r_m(x^{(k)})^T\end{bmatrix}(x-x^{(k)})+o(\lVert x-x^{(k)}\rVert)\\&=r(x^{(k)})+J(x^{(k)})(x-x^{(k)})+o(\lVert x-x^k\rVert)\end{aligned}$$

where $$J$$ is Jacobian of $$r$$ at $$x^{(k)}$$



Jacobian matrix of a function $$r:\mathbb{R}^n→\mathbb{R}^m$$

$$J(x)=\begin{bmatrix}\nabla r_1(x)^T\\ \vdots\\ \nabla r_m(x)^T\end{bmatrix}$$

is a $$n\times m$$ matrix\


“Gradient” of $$r:\mathbb{R}^n→\mathbb{R}^m$$

$$\nabla r(x)=J(x)^T$$



Goal: $$x^{(0)},x^{(1)},x^{(2)},…→x_t$$

1. $$\bar{r}^{(k)}(x)=r(x^{(k)})+J(x^{(k)})(x-x^{(k)})$$ linearization at $$x^{(k)}$$
2. $$\begin{aligned} x^{(k+1)} & = \underset{x}{\argmin} \frac{1}{2} \lVert r(x^{(k)})+J(x^{(k)})(x-x^{(k)})\rVert^2 \\ & = \argmin \frac{1}{2} \lVert J(x^{(k)})x-(J(x^{(k)})\cdot x^{(k)}-r(x^{(k)})) \rVert^2 \\&= \argmin\frac{1}{2}\lVert A_kx-b_k\rVert^2\end{aligned}$$

where $$A_k=J(x^{(k)})$ and $b_k=A_k\cdot x^{(k)}-r(x^{(k)})$$

i.e., $$x^{k+1}=A_k \backslash b_k$$



**pseudo-code for Gauss-Newton**

$$x^{(0)} \in \mathbb{R}^n$$ given; $$\varepsilon > 0$$ given

for $$k=0,1,2,3,…$$

$$x^{(k+1)} = A_k \backslash b_k$$

where $$A_k=J(x^{(k)})$$, $$b_k=A_kx^{(k)}-r(x^{(k)})$$

if $$\lVert x^{(k+1)}-x^{(k)}\rVert < \varepsilon$$, exit

return $$x^{(k+1)}$$

<figure><img src=".gitbook/assets/image (24).png" alt=""><figcaption><p>Gauss-Newton Implementation</p></figcaption></figure>

Least-Squares: $$x$$ is optimal for $$\min\frac{1}{2} \Vert Ax-b \rVert^2$$ iff $$A^T(Ax-b)=0$$ or $$A^Tr=0$$.
