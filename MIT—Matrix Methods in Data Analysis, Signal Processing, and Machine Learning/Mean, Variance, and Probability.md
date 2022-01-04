# Mean

We have two different situations that you have to keep straight. On the one hand, we may have the results (*sample values*) from a completed trial. On the other hand,  we may have the expected results (*expected values*) from future trial.

**Sample mean:** We've done the experiment, so we can use actual sample outputs.
$$
\mu = \frac{1}{N}(x_1+x_2+…+x_N)
$$
**Expected mean:** We know probabilities, but we haven't used them yet (before the experiment).
$$
E[X] =p_1x_1+p_2x_2+…+p_nx_n
$$

# Variance

**Sample variance** measures actual distance from the sample mean.
$$
S^2=\frac{1}{N-1}[(x_1-m)^2+…+(x_N-m)^2]
$$
For some wonderful reason in statistics, we divide by $N-1$ this time. One degree of freedom is already accounted for in the sample mean.

**Variance** measures expected distance from the expected mean.
$$
\sigma ^2 =E[(x-m)^2]=p_1(x_1-m)^2+...+p_n(x_n-m)^2
$$
Another way to compute the variance $\sigma^2$ :
$$
\begin{eqnarray}
Variance &=& E[(x-m)^2] \\
&=& p_1(x_1-m)^2+...+p_n(x_n-m)^2\\
&=& p_1(x_1^2-2x_1m+m^2)+...+p_n(x_n^2-2x_nm+m^2)\\
&=& p_1x_1^2+...+p_nx_n^2-2m(p_1x_1+...+p_nx_n)+(p_1+p_2+...+p_n)m^2\\
&=& E[X^2]-2m^2+m^2=E[X^2]-E[X]^2
\end{eqnarray}
$$

### Two useful inequality

#### 1. Markov's inequality

Suppose we know the average value (the mean $\overline{X}=E[X]$) of a random variable $X$ . What we want to know is something about its probabilities : the probability that $X$ is greater than or equal to $a$.

**Markov's inequality** assumes that all $x_i\geq0$ (*no samples are negative*) , then  
$$
P[X\geq a]\leq \frac {\overline{X}}{a} = \frac {mean\ of\ X}{a}=\frac{E[X]}{a}\tag{1}
$$
For example, suppose the numbers 0,1,2....(*all nonnegative*) appear with probabilities $p_0$​, $p_1$, 

$p_2$....And suppose that this distribution has mean $E[X]=\overline{X}=1$ :
$$
\overline{X}=0p_0+1p_1+2p_2+3p_3+4p_4+5p_5…=1\tag{2}
$$
Then Markov's equality with $a=3$ says that the probability of $X\geq3$ is most $\frac{1}{3}$ :
$$
p_3+p_4+p_5+…\leq \frac{E[X]}{a} =\frac{1}{3}\tag{3}
$$
***Proof:***   with equation(2) :
$$
0p_0+1p_1+2p_2+3(p_3+p_4+p_5+…)+p_4+2p_5+…=1\tag{4}
$$
Every term in equation(4) is greater than or equal to 0. Therefore:
$$
3(p_3+p_4+p_5+…)\leq 1
$$
which is Markov's inequality (3).

#### 2. Chebyshev's inequality

This applies to all random variables $X(s)$, not just to nonnegative functions. It provides an estimate for the probability of events that are far from the mean $\overline{X}$, the probability of $|X-\overline{X}| \geq a$ will decrease as the number $a$ increase. 

**Chebyshev's inequality** for any probability distribution (no assumption $x_i\geq0$) :
$$
P(|X-\overline{X}|\geq a)\leq \frac{\sigma^2}{{a_2}}
$$

***Proof:***  apply Markov's inequality to the nonnegative function
$$
Y(s)=(X(s)-\overline{X})^2
$$
By the definition of variance, the mean of that function $Y$ is $\sigma^2$.

Then use Markov:
$$
P(Y(s)\geq a^2) =P((X-\overline{X})^2\geq a^2)\leq \frac{mean\ of\ Y}{a^2}=\frac{\sigma^2}{a^2}
$$

# Covariance Matrix

### joint probability

$p_{ij}$ = probability that experiment 1 produces $x_i$ and experiment 2 produces $y_j$ 

### covariance

expected value of $(x-m_1)(y-m_2)$ :
$$
\sigma _{12}= \sum\limits_{i}\sum\limits_{j}p_{ij}(x-m_1)(y-m_2)
$$

### covariance matrix

$$
\begin{eqnarray}
V &=& \sum\limits_{i}\sum\limits_{j}p_{ij}
\begin{bmatrix}
x_i-m_1\\
y_i-m_2
\end{bmatrix}
\begin{bmatrix}
x_i-m_1 & y_i-m_2
\end{bmatrix}\\
&=& \sum\limits_{i}\sum\limits_{j}p_{ij}\begin{bmatrix}
(x_i-m_1)^2 & (x_i-m_1)(y_i-m_2)\\
(x_i-m_1)(y_i-m_2) & (y_i-m_2)^2
\end{bmatrix}\\
&=&\begin{bmatrix}
\sigma_1^2 & \sigma_{12}\\
\sigma_{12} & \sigma_2^2
\end{bmatrix}
\end{eqnarray}
$$

**note:** The covariance matrix is positive semidefinite. 
