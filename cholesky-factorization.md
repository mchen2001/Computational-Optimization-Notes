# Cholesky Factorization

* positive definite matrices
* computation and definition
* connection to Newton Method
* connection to Least-Squares

## Positive Definite Matrices

An $$n\times n$$ matrix $$A$$ (assume symmetric) is positive definite if (SPD)

$$x^TAx \gt 0, \forall x\in \mathbb{R}^n \ne 0$$

positive semi definite if (PSD)

$$x^TAx \ge 0, \forall x\in \mathbb{R}^n$$

negative definite matrix

$$x^TAx \lt 0, \forall x \ne 0$$

### Properties

1.  for any full rank $$n\times k$$ matrix $$X$$, $$X^TAX\gt 0$$ if $$A \gt 0$$         ①

    for all $$y\in \mathbb{R}^k$$ nonzero, $$0 \ne Xy$$ ⇒ $$y^T(X^TAX)y=\underbrace{(Xy)^T}_{\equiv Z^T}A(\underbrace{Xy}_{\equiv Z \ne 0})\gt 0$$

① ⇒ every principle sub-matrix of $$A$$ is also positive definite

<figure><img src=".gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

$$X^T_1AX_1=\begin{matrix}& P_1 & P_2 & P_3& \\ [& I & 0& 0&]\end{matrix}\begin{bmatrix}A_1 &&\\&A_2&\\&&A_3\end{bmatrix}\begin{bmatrix}I\\0\\0\end{bmatrix}=A_1$$

$$X_2^TAX_2=\begin{bmatrix}1 & 0 & \ldots &0 \end{bmatrix}A\begin{bmatrix}1\\0\\ \vdots \\0\end{bmatrix}=a_{11}$$

⇒ every diagonal element $$a_{ii} \gt 0$$

2. A is positive definite ↔ eigenvalues are positive

$$(x,\lambda)\in \mathbb{R}^n\times \mathbb{R}$$ is an eigen-pair of the matrix $$A$$ if

$$Ax=\lambda x$$

without loss of generality, $$\lVert x\rVert =1$$

⇒ $$0 \le x^TAx=x^T(\lambda x)=\lambda x^Tx=\lambda \lVert x\rVert^2=\lambda$$

> ➡️ If $$X\in \mathbb{C}^{n \times k}$$ (conjugate transpose)&#x20;
>
> If $$A$$ non symmetric: $$\frac{1}{2}(A+A^T)$$ is “symmetric part” of $$A$$

3. A is positive definite ↔ A has a Cholesky Decomposition

Make simplifying assumption that

![](<.gitbook/assets/image (35).png>)

**“Block” Gaussian Elimination:**

$$A=\begin{bmatrix}1&w^T\\ w&K\end{bmatrix}=\underbrace{\begin{bmatrix}1&0\\ w&I\end{bmatrix}}_{\equiv L}\begin{bmatrix}1&w^T\\ 0&K-w^T\end{bmatrix}$$

$$\begin{bmatrix}1&w^T\\0&K-ww^T\end{bmatrix}=\begin{bmatrix}1&0\\ 0&K-ww^T\end{bmatrix}\begin{bmatrix}1&w^T\\ 0&I\end{bmatrix}$$

$$\begin{aligned}A & = \begin{bmatrix}1&0\\ w&I\end{bmatrix}\begin{bmatrix}1&\\ &K-ww^T\end{bmatrix} \begin{bmatrix}1&w^T\\ 0&I\end{bmatrix} \\ &= L D L^T\end{aligned}$$

($$L^{-1}AL^{-T}=D$$) $$\overset{\text{By Property ①}}{⇒} K-ww^T \gt 0$$

Now, allow $$a_{11}$$ arbitrary (positive) $$\alpha := \sqrt{a_{11}}$$

$$A=\underbrace{\begin{bmatrix}\alpha&0\\ \frac{w}{\alpha}&I\end{bmatrix}}_{R_1^T}\underbrace{\begin{bmatrix}1&0\\0&K-\frac{ww^T}{\alpha}\end{bmatrix}}_{A_1}\underbrace{\begin{bmatrix}\alpha&\frac{w^T}{\alpha}\\ 0&I\end{bmatrix}}_{R_1}$$,

where <img src=".gitbook/assets/image (36).png" alt="" data-size="original">

Because $$K-ww^T/\alpha^2$$ is positive definite, it also has the factorization

$$\underbrace{k-ww^T/\alpha^2}_{(n-1)\times (n-1)}=\bar{R}^T_2\bar{A}_2\bar{R}_2$$

where ![](<.gitbook/assets/image (37).png>)

Cholesky Decomposition of $$A \gt 0$$

$$A=R^TR$$, $$R$$ is upper triangle

$$\begin{aligned}A =R^T_1A_1R_1 &= R^T_1\begin{bmatrix}1&0 \\ 0&\bar{R}^T_2\bar{A}_2\bar{R}_2\end{bmatrix}R_1 \\ &=R^T_1\begin{bmatrix}1&0 \\ 0&\bar{R}^T_2\end{bmatrix}\begin{bmatrix}1& \\ &\bar{A}_2\end{bmatrix}\begin{bmatrix}1&0 \\ 0&\bar{R}2\end{bmatrix}R_1 \\ &= R^T_1R^T_2A_2R_2R_1\\ (n-1) & \vdots \\ & = \underbrace{R^T_1R^T_2\ldots R^T_n}_{\text{lower triangle}}(I)\underbrace{R_nR_{n-1}\ldots R_1}_{\text{upper triangle}}\end{aligned}$$
