严平稳：
$$
F(x_1,\dots,x_n;t_1,t_2,\dots,t_n) = F(x_1,\dots,x_n;t_1+\tau,\dots,t_n+\tau)
$$
宽平稳：

随机过程$\{X(t), t \in T\}$的一、二阶矩存在，若有数学期望$m_X(t)=m_X$，且满足：$R_X(t,t+\tau)=R_X(\tau)$与$t$无关，则称$\{X(t), t \in T\}$为弱平稳/宽平稳随机过程。

* 严平稳不一定是宽平稳的；但二阶矩严平稳一定是宽平稳
* 宽平稳一般推不出他是严平稳

定理：正态过程的严平稳和宽平稳等价

## 数字特征：

$$
m_X(t)=m_X \\
R_X(t_1,t_1+\tau) = R_X(t_1-t_2) = R_X(\tau) \\
C_X(t,t+\tau) = R_X(t,t+\tau)-m_X(t)m_X(t+\tau) = R_X(\tau)-m_X^2 = C_X(\tau) \\
D_X(t) = C_X(t,t) = C_X(0) = R_X(0) - m^2_X
$$

例1：正态白噪声
