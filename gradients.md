# Gradients

$$f: \R^n \to \R$$

Assume $$i^{th}$$-partial derivative exists:

$$\frac{\delta f(x)}{\delta x_i} = \underset{\varepsilon→0}{lim}\frac{f(x+\varepsilon e_i)-f(x)}{\varepsilon}$$

$$e_i=\begin{bmatrix} 0 \\ \vdots \\ 1 \\ 0\\ \vdots \\ 0\end{bmatrix}$$i$$^{th}$$ position                    <img src=".gitbook/assets/Untitled (2).png" alt="" data-size="original">

The gradient of $$f$$ is the collection of partials:

$$
\nabla f(x)= \begin{bmatrix}\delta f(x)/\delta x_1\\ \delta f(x)/\delta x_2 \\ \vdots\\ \delta f(x)/\delta x_n\end{bmatrix} \in \mathbb{R}^n
$$

### Directional derivative of  at $$x\in \R^n$$&#x20;

in the direction $$d \in \R^n$$

$$f’(x,d)=\underset{\varepsilon → 0}{lim}\frac{f(x+\varepsilon d)-f(x)}{\varepsilon}$$

The function $$f$$ is differentiable of $$x \in \R^n$$ if $$f’(x,d)$$ exists for all of $$\R^n$$, and $$f’(x,d)=\nabla f(x)^Td$$

> **Fact**: the direction derivative is positively homogeneous of degree 1, i.e., $$f’(x,\alpha d)=\alpha f’(x,d), \forall \alpha≥0$$

Special Directions

$$d=\begin{bmatrix}d_1 \\ d_2 \\ \vdots \\ d_n \end{bmatrix}$$→ $$d=e_i$$

$$f’(x,e_i)=\nabla f(x)^Te_i=[\nabla f(x)]_i=\frac{\delta f(x)}{\delta x_i}$$

### Calculus Rules for $$\R^n$$

$$f:\mathbb{R}^n→\mathbb{R}$$

Linear function: $$f(x)=a^Tx=\sum^{n}_{i=1}a_ix_i$$

$$\nabla f(x)=\begin{bmatrix}a_1\\a_2\\ \vdots\\ a_n \end{bmatrix}=a$$

**Quadratic functions:**

$$f(x)=x^TQx+c^Tx+\alpha$$

$$Q$$ is $$n\times n$$ matrix, $$c\in \mathbb{R}^n$$ and $$\alpha \in \mathbb{R}$$

$$\nabla f(x)=Qx+Q^Tx+c=(Q+Q^T)x+c$$



If $$Q$$ is symmetric, i.e., $$Q=Q^T$$, $$\nabla f(x)=2Qx+c$$

WLOG, assume $$Q$$ symmetric.



If not, observe:

$$\begin{aligned}f(x) &=x^TQx+c^Tx+\alpha\\ &=\frac{1}{2}x^TQx+\frac{1}{2}x^TQx+c^Tx+\alpha\\ &=\frac{1}{2}x^TQ^Tx+\frac{1}{2}x^TQx+c^Tx+\alpha \\ &=x^T(\frac{1}{2}Q^T+\frac{1}{2}Q)x+c^Tx+\alpha \\ &=x^T\overline{Q}x+c^Tx+\alpha\end{aligned}$$

where $$\overline{Q}=\frac{1}{2}Q^T+\frac{1}{2}Q$$, called “symmetric part of $$Q$$”

**Directional Derivative:**

$$f’(x,d)=\nabla f(x)^Td$$

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

### Computing Gradients

1. Numerical → ”finite differencing”
2. Symbolic
3. Automatic Differentiation

**Numerical:**

Taylor’s Theorem:

$$f(x+\varepsilon d)=f(x)+\varepsilon \nabla f(x)^Td+O(\varepsilon)$$, $$g \in O(\varepsilon) \text{ if } \underset{\varepsilon \to 0}{\lim}\frac{g(\varepsilon)}{\varepsilon}=0$$

$$f’(x;d)=\nabla f(x)^Td \cong \frac{f(x+\varepsilon d)-f(x)}{\varepsilon}$$

Choose $$d=e_i$$

$$\frac{\delta f(x)}{\delta x_i} \cong \frac{f(x+\varepsilon e_i)-f(x)}{\varepsilon}$$ “forward finite differencing”



**Central Differencing:**

$$\frac{\delta f(x)}{\delta x_i}=\frac{f(x+\varepsilon e_i)-f(x-\varepsilon e_i)}{2\varepsilon}+O(\varepsilon^2)$$



**Symbolic Differentiation**

1. $$\frac{\delta}{\delta x}(f_1(x)+f_2(x))=\frac{\delta}{\delta x}f_1(x)+\frac{\delta}{\delta x} f_2(x)$$
2. $$\frac{\delta}{\delta x}(f_1(x) \cdot f_2(x))=(\frac{\delta}{\delta x}f_1(x))f_2(x)+(\frac{\delta}{\delta x}f_2(x))f_1(x)$$
3. $$\frac{\delta}{\delta x} f_1(f_2(x))= \frac{\delta}{\delta f_2(x)}f_1(f_2(x)) \cdot \frac{\delta}{\delta x} f_2(x)$$

$$f:\mathbb{R}^n→\mathbb{R}$$

$$\nabla f(x)=\begin{bmatrix}\frac{\delta f(x)}{\delta x_1}\\ \vdots \\ \frac{\delta f(x)}{\delta x_n}\end{bmatrix}$$

Example $$f(x_1,x_2)=\ln(x_1)+x_1x_2-\sin(x_2)$$

$$\frac{\delta f(x_1,x_2)}{\delta x_1}=\frac{1}{x_1}+x_2$$

$$\frac{\delta f(x_1,x_2)}{\delta x_2}=x_1-\cos(x_2)$$



**Computational Graph**

<figure><img src=".gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

input $$(x_1,x_2)=(2,5)$$

$$v_1=x_1=2$$

$$v_2=x_2=5$$

$$v_3=\ln(v_1)=\ln(2)$$

$$v_4=v_1 \cdot v_2 = 2 \cdot 5 = 10$$

$$v_5 = \sin(v_2)=\sin(5)=-0.96$$

$$v_6=v_3+v_4=10.69$$

$$v_7=v_6-v_5=11.65$$

$$y=v_7$$



Forward Mode Auto Diff

Let $$\dot{v}_i=\frac{\delta v_i}{\delta x_1}$$ (for gradient with respect to $$x_1$$, repeat for $$x_2$$)

$$\dot{v}_1=\frac{\delta v_1}{\delta x_1} = 1$$

$$\dot{v}_2=\frac{\delta v_2}{\delta x_1} = 0$$

$$\dot{v}_3=\frac{\delta v_3}{\delta x_1}=\frac{\delta v_3}{\delta v_1}\cdot \frac{\delta v_1}{\delta x_1}=\frac{\delta v_3}{\delta v_1}\dot{v}_1=\frac{1}{v_1}\cdot \dot{v}_1=\frac{1}{2}$$

$$\dot{v}_4=\frac{\delta v_4}{\delta x_1}=\frac{\delta v_4}{\delta v_1}\cdot \frac{\delta v_1}{\delta x_1}+\frac{\delta v_4}{\delta v_2} \cdot \frac{\delta v_2}{\delta x_1}=\frac{\delta v_4}{\delta v_1}\cdot \dot{v}_1+\frac{\delta v_4}{\delta x_2}\dot{v}_2=5$$

$$\dot{v}_5=\cos(v_2)\cdot \dot{v}_2=0$$

$$\dot{v}_6=\dot{v}_3+\dot{v}_4=\frac{1}{2}+5$$

$$\dot{v}_7=\dot{v}_6-\dot{v}_5=5.5-0=5.5$$



Reverse Mode Auto Diff

Let $$\bar{v}_i=\frac{\delta y}{\delta v_i}$$ ("adjoint")

$$\bar{v}_7=\frac{\delta y}{\delta v_7}=1$$

$$\bar{v}_6=\frac{\delta y}{\delta v_6}=\frac{\delta y}{\delta v_7}\cdot \frac{\delta v_7}{\delta v_6}=\bar{v}_7\cdot \frac{\delta v_7}{\delta v_6}=1\cdot 1=1$$

$$\bar{v}_5=\frac{\delta y}{\delta v_5}=\frac{\delta y}{\delta v_7}\cdot\frac{\delta v_7}{\delta v_5}=1\cdot(-1)=-1$$

$$\bar{v}_4=\frac{\delta y}{\delta v_4}=\bar{v}_6\cdot \frac{\delta v_6}{\delta v_4}=1\cdot 1=1$$

$$\bar{v}_3=\frac{\delta y}{\delta v_3}=\bar{v}_6\cdot\frac{\delta v_6}{\delta v_3}=1\cdot1=1$$

$$\bar{v}_2=\frac{\delta y}{\delta v_2}=\bar{v}_4\cdot\frac{\delta v_4}{\delta v_2}+\bar{v}_5\frac{\delta v_5}{\delta v_2}=2+(-1)\cdot cos(5)=2-0.28=1.72$$

$$\frac{\delta f(x_1,x_2)}{\delta x_1}=\frac{\delta y}{\delta v_1}=\bar{v}_1=\bar{v}_3\cdot\frac{\delta v_3}{\delta v_1}+\bar{v}_4\cdot\frac{\delta v_4}{\delta v_1}=1\cdot\frac{1}{2}+1\cdot 5=5.5$$
