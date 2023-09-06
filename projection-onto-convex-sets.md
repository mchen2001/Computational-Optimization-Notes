# Projection Onto Convex Sets

$$
x_{LS}=\underset{x\in\R^n}{\min}\frac{1}{2}\lVert Ax-b\rVert^2
$$

where $$A$$ is $$m\times n$$.

<figure><img src=".gitbook/assets/image (21).png" alt=""><figcaption><p><span class="math">Ax_{LS}</span> projection of <span class="math">b</span> onto <span class="math">range(A)</span></p></figcaption></figure>

$$
\min \frac{1}{2} \lVert Ax-b\rVert^2 \Leftrightarrow \min \frac{1}{2} \lVert z-b\rVert^2 \text{ subject to } z\in range(A)
$$

Then (“orthogonal” or “Euclidean”) projection of a vector $$b\in \R^n$$ onto $$C\subseteq \R^n$$ convex is the solution of the convex optimization problem

$$
proj_C(b)=\underset{z\in\R^n}{\min}\frac{1}{2}\lVert z-b\rVert^2 \text{ subject to } z\in C
$$

* Convex optimization problem
* Objective is strictly convex ⇒ solution is unique

### Properties of $$\text{proj}_C(b)$$

* if $$b\in C$$ ⇒ $$proj_C(b)=b$$
* $$proj_C(b)$$ is unique
* $$z=proj_C(b)$$ ↔ $$(b-z)^T(y-z)\le 0, \forall y\in C$$

<figure><img src=".gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

$$-\nabla f(z)\in N_C(z)$$

$$b-z \in N_C(z)$$ $$\overset{\text{use definition of Normal Cone}}{\Leftrightarrow}(b-z)^T(y-z)\le 0, \forall y\in C$$
