## Schur标准形：酉相似上三角化、正规阵的酉相似对角化

### 一、Schur定理

1、定理：$\forall A \in \mathbb{C}^{n\times n}$, 存在酉阵U，使得 $U^{-1}AU$ 为上三角阵

2、证明：数学归纳法

3、分块Schur三角化定理

4、Cayley-Hamilton定理：设A的特征多项式为$f(\lambda)$，则有$f(A)=0$，若AB相似，则$f(A)=f(B)$

5、存在可逆阵P，使得 $P^{-1}BP=\begin{bmatrix}
B_1 & 0 & 0 \\
0 & B_2 & 0 \\
0 & 0 & B_s
\end{bmatrix}$

### 二、酉相似对角化

1、定理：设$A\in \mathbb{C}^{n\times n}$，则以下条件等价：

(1) 存在酉阵U，使得$U^{-1}AU=B=D$，对角阵

(2) A是正规的(normal): $A^HA=AA^H$

## 相似标准形——Jordan标准形、求Jordan标准形、化Jordan标准形、应用

### 一、相似不变量

6、A的最小多项式是使得m(A)=0的，次数最低的，首项系数为1的多项式m(x)，记作mA(x)

注：

1. 三阶幂零矩阵如下所示，n阶幂零矩阵的最小多项式$m(x)=x^n$
    $$
    \begin{bmatrix}0 & 1 & 0 \\0 & 0 & 1 \\0 & 0 & 0\end{bmatrix}
    $$

2. 由于f(A)=0，且f(A)是n次多项式，则$A^n$可由较低次幂的线性组合给出，更高次幂也可由其低于n次的幂的线性组合给出：
    $$
    A^m \in {\rm span} \{I,A, A^2, \dots,A^{n-1}\}
    $$

### 二、Jordan标准形

1、定理：设$A\in \mathbb{C}^{n\times n}$，则存在可逆阵P，使得$P^{-1}AP=J$

### 三、计算Jordan标准形