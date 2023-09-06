# Stochastic Gradient Descent (SGD)

### Gradient Descent

$$\min_{x\in C}f(x)$$

$$f$$: convex differentiable $$C$$

objective function is an “expectation”

$$f(x)=\frac{1}{m}\left[f_1(x)+f_2(x)+\cdots+f_m(x)\right]=\mathbb{E}_i f_i(x)$$,

where $$i$$ is random variable uniform distributed over $$\left \{1,\cdots,m\right \}$$



**Example**: least-squares

$$\begin{aligned}f(x)&=\frac{1}{m}\left[\frac{1}{2}\lVert Ax-b\rVert_2^2\right] \\&=\frac{1}{m}\left[\frac{1}{2}\lVert \begin{bmatrix}a_1^T \\ \vdots \\ a_m^T\end{bmatrix}x-\begin{bmatrix}b_1 \\ \vdots \\ b_m\end{bmatrix}\rVert^2\right] \\ &=\frac{1}{m}\sum_{i=1}^m \frac{1}{2}(a_i^Tx-b_i)^2 \\ &=\frac{1}{m}\sum_{i=1}^mf_i(x)\end{aligned}$$

### Gradient Descent

$$x_{k+1}=x_k-\alpha_k\nabla f(x_k)$$

Main cost at each iteration $$k$$ is $$\nabla f(x_k)=\frac{1}{m}\sum_{i=1}^m\nabla f_i(x)$$

Ex: for LS,

$$\begin{aligned}\nabla f(x)&=\nabla \left[ \frac{1}{2}\lVert Ax-b\rVert^2\right] \\ &=A^T(Ax-b) \\ &=A^Tr \\ &=\begin{bmatrix}a_1 \cdots a_m\end{bmatrix}\begin{bmatrix}r_1 \\ \vdots \\ r_m\end{bmatrix}=\sum_{i=1}^m a_ir_i\end{aligned}$$

### Approximate the Gradient

randomly sample $$i\in\left \{1,\cdots,m\right \}$$

Stochastic gradient approx to $$\nabla f(x)$$ is $$g=\nabla f_i(x)$$

$$\begin{aligned}\mathbb{E}g & =\sum_{i=1}^m \frac{1}{m}\nabla f_i(x) \\ &=\frac{1}{m}\sum_{i=1}^m\nabla f_i(x) \\ &\equiv \nabla f(x)\end{aligned}$$



### Stochastic Gradient Method

$$x_{k+1}=x_k-\alpha_kg_k$$

cost at iteration $$k$$: choose $$i_k \in \left \{ 1,\ldots, m\right\}$$, compute $$g_k:=\nabla f_{i_k}(x)$$

Variant: instead of sampling single element $$\left \{1,\cdots,m\right \}$$, sample a “batch” $$B_k \subseteq \left \{ 1,\ldots, m\right \}$$

$$k$$th Stochastic gradient estimation: $$g_k=\frac{1}{\lvert B_k\rvert}\sum_{i\in B_k}\nabla f_i(x)$$

### Convergence of function values $$f(x_k)$$ in expectation:

$$f_k:=f(x_k)$$

$$\nabla f_k := \nabla f(x_k)$$

By the descent lemma, if $$f$$ has an L-Lip continuous gradient

$$\lVert \nabla f(x)-\nabla f(y)\rVert_2 \le L\cdot \lVert x-y\rVert_2$$ for some $$L \gt 0, \forall x,y$$

$$f(z)\le f(x)+\nabla f(x)^T(z-x)+\frac{L}{2}\lVert z-x\rVert^2, \forall x,z$$

so take $$z=x_{k+1}$$, $$x=x_k$$:

$$f_{k+1}\le f_k+\nabla f_k^T(x_{k+1}-x_k)+\frac{L}{2}\lVert x_{k+1}-x_k\rVert^2$$

SGD: $$x_{k+1}=x_k-\alpha g_k$$ ⇒ $$x_{k+1}-x_k=-\alpha g_k$$

⇒ $$f_{k+1}\le f_k-\alpha \nabla f_k^Tg_k+\frac{L\alpha^2}{2}\lVert g_k\rVert^2$$



Take expectations of both sides:

$$\begin{aligned}\mathbb{E}f_{k+1} &\le \mathbb{E}f_k-\alpha\mathbb{E}\lVert \nabla f_k\rVert^2+\frac{L\alpha^2}{2}\mathbb{E}\lVert g_k\rVert^2 \\ &\le \mathbb{E}f_k-\alpha\mathbb{E}\lVert \nabla f_k\rVert^2+\frac{L\alpha^2}{2}(\sigma^2+\mathbb{E}\lVert \nabla f_k\rVert^2) \\ &\le \mathbb{E}f_k-\alpha(1-\frac{L\alpha}{2})\mathbb{E}\lVert \nabla f_k\rVert^2+\frac{L\alpha^2\sigma^2}{2} \\ &\le \mathbb{E}f_k-\frac{\alpha}{2}\mathbb{E}\lVert \nabla f_k\rVert^2+\frac{L\alpha^2\sigma^2}{2} \text{ if } \alpha \le \frac{1}{L}...\end{aligned}$$



Assumption: need to assume mean-squared error in stochastic approx is bounded:

$$\mathbb{E}\left[\lVert g_k-\nabla f_k \rVert^2\right]=\mathbb{E}\left[\lVert g_k\rVert^2\right]-\lVert \nabla f_k\rVert^2 \le \sigma^2 ,\forall k$$

for some $$\sigma \gt 0$$ fixed ⇒ $$\mathbb{E}\left[\lVert g_k\rVert^2\right] \le \sigma^2+\lVert \nabla f_k\rVert^2$$



Sum and reverse for all $$k=0,1,2,\cdots,T$$

$$\mathbb{E}f_k \le f(x_0)-\frac{\alpha}{2}\sum_{k=1}^{T-1}\mathbb{E} \left[\lVert \nabla f_k \rVert^2\right]+\frac{\alpha^2\sigma L T}{2}$$

Divide both sides by $$\alpha \frac{T}{2}$$,

$$\frac{1}{T}\sum_{k=0}^{T-1}\mathbb{E} \lVert \nabla f_k\rVert^2 \le\frac{2(f(x_0)-f^*)}{\alpha T}+\underbrace{\alpha \sigma L}_{\text{error term}}$$.
