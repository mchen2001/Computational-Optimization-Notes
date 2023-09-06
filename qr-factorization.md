# QR Factorization

* numerical method (standard) for LS probs
* properties of QR
* numerical benefits
* computation

In general, $$\lVert(a,b)\rVert^2=(a,b)^T(a,b)=a^Ta+b^Tb=\lVert a\rVert^2+\lVert b\rVert^2$$

### Linear Least Squares

$$\min \frac{1}{2}\lVert Ax-b\rVert^2_2$$

if A has full col rank ($$m>n$$) then $$X_{LS}$$ uniquely solves Normal Equation’s

$$A^TAx_{LS} = A^Tb$$

$$x_{LS} = (A^TA)^{-1}A^Tb$$

$$\bar{y}=Ax_{LS}=A(A^TA)^{-1}A^Tb$$ (projector onto $$range(A)$$)

“Conditioning” of a matrix determines the accuracy of a linear system solve: $$cond(M)=\frac{\lambda_{max}(M)}{\lambda_{min}(M)}$$

If $$M$$ is not square:

$$cond(M)=\frac{\nabla{max}(M)}{\nabla{min}(M)}$$, where $$\nabla$$ is the gradient

For $$M = A^TA$$, $$\nabla(M) = \nabla(A^TA)=\nabla(A)^2$$

$$\lambda_i(A^TA)=\nabla_i(A)^2$$



With $$Q$$ be orthogonal basis for $$range(A)$$

$$\underbrace{Q^T}_{n \times m}\underbrace{Q}_{m \times n}=\underbrace{I}_{n\times n}$$

$$P$$ is an orthogonal projector onto $$range(P)$$ if

1. $$P^2=P$$ idempotent
2. $$P=P^T$$ symmetric

Take $$P=QQ^T$$: $$range(P)=range(Q)=range(A)$$

$$P^2=QQ^TQQ^T=QQ^T=P$$



$$range(Q) = range(A)$$

$$Q=[q_1,q_2,…,q_n]$$

$$span\{q_1,…,q_n\}=span\{a_1,…,a_n\}$$



Every matrix $$A_{m\times n}$$ has a QR Factorization:

$$A=Q\begin{bmatrix} R \\ 0 \end{bmatrix}$$, where $$Q$$ is orthogonal ($$QQ^T=Q^TQ=I$$) and R=upper triangular

<figure><img src=".gitbook/assets/Untitled (1).png" alt=""><figcaption></figcaption></figure>

$$Q$$ is orthogonal (and square)

$$Q^TQ=Q^TQ=I_m$$

$$Q_1$$ is orthonormal (not orthogonal)

$$Q_1^TQ_1=I_n$$

$$Q_1Q_1^T \ne I_m$$

orthonormal matrices are rotations:

1. for any vector $$x \in \R^n$$, $$\lVert Q_1x\rVert_2=\lVert x\rVert_2$$ ⇒ $$\lVert Q_1x\rVert^2=x^TQ_1^TQ_1x=x^Tx=\lVert x\rVert^2$$
2. any $$y \in \R^m$$, $$(Qx)^T(Qy)=x^TQ^TQy=x^Ty$$

### Solving Least Squares

$$\underset{x}{\min}\lVert Ax-b\rVert^2$$

$$\begin{aligned} \lVert Ax-b \rVert ^2 &=\lVert Q^T(Ax-b)\rVert ^2 \\ &=\lVert Q^TAx-Q^Tb\rVert ^2 \\ &=\lVert \begin{bmatrix} Rx\\ \hdashline \\ 0\end{bmatrix}-\begin{bmatrix} Q^T_1b\\ \hdashline \\ Q^T_2 b\end{bmatrix}\rVert ^2 \\ &= \lVert Rx-Q^Tb\rVert^2+\lVert Q^T_2b\rVert^2\end{aligned}$$

$$A = Q\begin{bmatrix}R \\ 0\end{bmatrix}$$

Multiply both sides on the left with $$Q^T$$

$$Q^TA=\underbrace{Q^TQ}_I\begin{bmatrix}R\\0\end{bmatrix}$$

$$\begin{bmatrix}Q^T_1A\\Q_2^TA\end{bmatrix}=\begin{bmatrix}R\\0\end{bmatrix}$$

$$Q_1^TA=R$$

$$Q_2^TA=0$$

$$R_1x=Q_1^Tb$$ ⇒ solving least squares using QR

$$\begin{aligned}Cond(A) &= Cond(Q,R)\\ &= Cond(R)\end{aligned}$$
