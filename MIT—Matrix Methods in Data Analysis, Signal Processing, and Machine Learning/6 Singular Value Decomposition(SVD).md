# Lecture 6: Singular Value Decomposition(SVD)

## SVD and its proof

When A is rectangular, $Ax=\lambda x$ is impossible, left part is in $m$ dimensions, right part is in $n$ dimensions for $A \in \mathbb{R}^{m \times n}, x \in \mathbb{R}^{n}$.

When $A$ is square, its evalues maybe complex, evectors are not orthogonal, we cannot stay with evalues.

Compare with $S = Q\Lambda Q^T$(S is a symmetric matrix, Q is orthogonal, eigenvalues are real number)

Now let's see the case A is ==rectangular==:
$$
A = U\Sigma V^T
$$
where u and v are ==singular vectors==, $\Sigma = \begin{bmatrix} \sigma_1 &  & & \\  & \sigma_2 &  \\ &  & ...\\ &&&\sigma_r \end{bmatrix}$. $\sigma_i$ s are ==singular values==,  they are positive or zero.

**Any** matrix $A$ can be factored into $U\Sigma V^T$, which is parallel to the spectral theorem that any symmetric matrix $S$ could be factored as $Q \Lambda Q^T$.

Let's see what are the $U$, $\Sigma$, $V$ truly means.

**What we have**

 $A_{m\times n}$ is rectangular,  Then $A^TA_{n\times n}$  is square and symmetric and PD, so we have:
$$
A^TA_{n\times n} = V\Lambda V^T
$$
 $AA^T_{m\times m}$  is also square and symmetric, and $AA^T_{m\times m}$  has the same non-zero evalues with  $A^TA_{n\times n}$ , so we have:
$$
A^TA_{n\times n} = U\Lambda U^T
$$
**Looking for a bunch of orthogonal vectors $v$**
$$
Av_1 = \sigma_1 u_1\\
...\\
Av_r = \sigma_r u_r\\
Av_{r+1} = 0\\
...
$$
The picture goes with the equations:

<img src="6 Singular Value Decomposition(SVD).assets/image-20210812153913435.png" alt="image-20210812153913435" style="zoom:40%;" />

v and u are orthogonal in their own spaces, and by multipling A, v becomes u.

Matrix form:
$$
A\begin{bmatrix} | &  & | \\ v_1 & ... & v_r \\ | &  & | \end{bmatrix} = \begin{bmatrix} | &  & | \\ u_1 & ... & u_r \\ | &  & | \end{bmatrix}\begin{bmatrix} \sigma_1 &  &  \\  & ... &  \\  &  & \sigma_r \end{bmatrix}
$$

$$
AV=U\Sigma\ \rightarrow \ A = U\Sigma V^T
$$

$$
A^TA = (U\Sigma V^T)^T(U\Sigma V^T) = V(\Sigma^T\Sigma)V^T
$$

$$
AA^T = (U\Sigma V^T)(U\Sigma V^T)^T = U(\Sigma\Sigma^T)U^T
$$

So we now know that V are the eigenvectors of $A^TA$, U are the eigenvectors of $AA^T$

and $\sigma^2$ are the eigenvalues of $A^TA$ and $AA^T$

So
$$
u_1 = \frac{Av_1}{\sigma_1}\\...\\
u_r =\frac{Av_r}{\sigma_r}
$$
We have a whole plane of possibility of u, and we want u to be correct.



We want to prove that, $u_1,...,u_r$ are orthogonal, giving that v's are orthogonal eigenvectors of $A^TA$

That is
$$
u_i^Tu_j=0,\ i\neq j
$$
then
$$
(\frac{Av_i}{\sigma_i})^T\frac{Av_j}{\sigma_j}=\frac{v_i^TA^TAv_j}{\sigma_i\sigma_j}
$$
Giving that $v_j$ is eigenvector of $A^TA$,
$$
\frac{v_i^TA^TAv_j}{\sigma_i\sigma_j}=\frac{v_i^T\sigma_2^2v_j}{\sigma_i\sigma_j} = 0
$$
So U is orthogonal.



## Geometry

$$
Ax = U\Sigma V^Tx
$$

Supposed that $\sigma_1\ge \sigma_2\ge...\ge\sigma_r>0$
$$
x\rightarrow V^Tx\ (reflection\ or\ rotation)\rightarrow\Sigma V^Tx\ (stretch: circle\ to \ ellipse)\rightarrow U\Sigma V^Tx\ (reflection\ or\ rotation)
$$
Operation A is shown  in the picture

<img src="6 Singular Value Decomposition(SVD).assets/image-20210812162207263.png" alt="image-20210812162207263" style="zoom:50%;" />

Every matrix multiplication factors into a rotation times a stretch times a different rotation.

**Q: When is u the same as v?** 

A: 

Compared $S = Q\Lambda Q^T$ with $A = U\Sigma V^T$.

When A is square, ==symmetric== and ==positive definite==.



## Count the parameters

Supposed that A in **two by two cas**e:
$$
A = \begin{bmatrix} a& b \\  c&d  \end{bmatrix}
$$
We have 4 elements for A and 4 parameters: **1** for rotation U, **2** for Stretching $\Sigma$ (See, $2\times 2$ case has 2 singular values), **1** for rotation V.



when it is in **three by three case**:
$$
A = \begin{bmatrix} &&\\  &9\ params& \\&& \end{bmatrix}
$$
9 elements and 9 params. Rotation in 3D has three params: ==roll, pitch and yaw== (apparently pilot conceptions lol) 



The product of eigenvalues equals to the determinnant. (in square case)

The product of singular values equals to the determinnant as well.

> Orthogonal matrix's determinant is one.



## Two representations

A has a small size and a large size.
$$
A =
\begin{bmatrix} | &  & | \\ u_1 & ... & u_r \\ | &  & | \end{bmatrix}\begin{bmatrix} \sigma_1 &  &  \\  & ... &  \\  &  & \sigma_r \end{bmatrix}\begin{bmatrix}  -& v_1^T &-  \\  & ... & \\ - & v_r^T & - \end{bmatrix}\\
=\begin{bmatrix} | &  & | \\ u_1 & ... & u_m \\ | &  & | \end{bmatrix}_{m\times m}
\begin{bmatrix} \sigma_1 &  &  \\  & ... &  \\  &  & \sigma_r \\&&&0\\&&&&...\\&&&&&0\end{bmatrix}_{m\times n}
\begin{bmatrix}  -& v_1^T &-  \\  & ... & \\ - & v_n^T & - \end{bmatrix}_{n\times n}
$$


## Polar decomposition

Polar is the real guy.

Inspired by polar representation of a complex number:
$$
c = re^{i_\theta}
$$
We get a polar decomposition of A:
$$
A = SQ
$$
symmetric matrix times orthogonal matrix

We can get a polar decomposition quickly out of the SVD.
$$
A =U\Sigma V^T=(U\Sigma U^T) (UV^T) = SQ
$$

> Enginnering experience:
>
> An erastic thing has a symmetric kind of stretch and a internal twist.



## Connection with data science

What data science do is finding the important part of a big matrix A, some part of it is noise and some part is signal.

**Q: What is the principle component?**

A: It should be the ordered rank-1 matrixs.

**In SVD:** 
$$
A =
\begin{bmatrix} | &  & | \\ u_1 & ... & u_r \\ | &  & | \end{bmatrix}\begin{bmatrix} \sigma_1 &  &  \\  & ... &  \\  &  & \sigma_r \end{bmatrix}\begin{bmatrix}  -& v_1^T &-  \\  & ... & \\ - & v_r^T & - \end{bmatrix}\\
=\begin{bmatrix} | &  & | \\ u_1 & ... & u_m \\ | &  & | \end{bmatrix}_{m\times m}
\begin{bmatrix} \sigma_1 &  &  \\  & ... &  \\  &  & \sigma_r \\&&&0\\&&&&...\\&&&&&0\end{bmatrix}_{m\times n}
\begin{bmatrix}  -& v_1^T &-  \\  & ... & \\ - & v_n^T & - \end{bmatrix}_{n\times n}\\
=u_1\sigma_1v_1^T + \dots
$$
(To be continue in next class....lol)