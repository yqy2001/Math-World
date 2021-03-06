# Background : Taylor series

#### One function *F*, one variable *x* :

$$
F(x+\Delta x)\approx F(x)+\Delta x \frac{dF}{dx}+\frac{1}{2}(\Delta x)^2\frac{d^2F}{dx^2} \tag{1}
$$

#### One function *F*, n variables *x* ($x=x_1, x_2...x_n$):

$$
F(x+\Delta x)\approx F(x)+(\Delta x)^T \nabla F+\frac{1}{2}(\Delta x)^T H (\Delta x)\tag{2}
$$

The vector $\nabla F$ is the gradient of $F$ , which is $\nabla F=\begin{bmatrix} \frac {\partial F}{\partial x_1} \\\frac {\partial F}{\partial x_2} \\ \cdots \\ \frac {\partial F}{\partial x_n} \end{bmatrix}$.

The matrix $H$ is the Hessian matrix,  which is the symmetric matrix of second derivatives $H_{ij}=\frac{\partial^2 F}{\partial x_i \partial x_j}=\frac{\partial^2 F}{\partial x_j \partial x_i}$.

#### n functions *f* ($f=f_1, f_2...f_n$), n variables *x* ($x=x_1, x_2...x_n$):

That's what exactly what you have in the gradient $\nabla F$ ——n funs, n vars.
$$
f(x+\Delta x)\approx f(x)+J\Delta x\tag{3}
$$
The symbol $J$ represents the **Jacobian matrix**, $J_{jk}=\frac{\partial f_j}{\partial x_k}$.

# Newton's method

We try to minimize $F(x)$, which is equivalent to solving $f=\nabla F=0$. Suppose we are at the point $x_k$, we want to get a new point $x_{k+1}$. With equation(3) :
$$
0=f(x_{k+1})=f(x_k+J(x_k)(x_{k+1}-x_k))
$$
which can be rewritten as: 
$$
x_{k+1}=x_k - J(x_k)^{-1}f(x_k)\tag{4}
$$
So that's **Newton's methods**.

Suppose we only have one function $f(x)=x^2-9$, and we want to solve $f(x)=0$. Of course,  $J(x)=2x$ . So what is Newton's method for it? 

Newton's method says (*with equation(4)*): 
$$
x_{k+1}=x_k-\frac{1}{2x_k}(x_k^2-9)=\frac{1}{2}x_k+\frac{9}{2}\frac{1}{x_k}
$$
We know the answer is 3, so now we're looking at the error, which is we hope approaching to 0. Subtracted 3 from both sides:
$$
x_{k+1}-3=\frac{1}{2}x_k+\frac{9}{2}\frac{1}{x_k}-3=\frac{1}{2x_k}(x_k-3)^2
$$
There will still be an error in the new $x_{k+1}$, but that error is proportional to the square of the error in $x_k$. If $x_k$ is close to $x^*$, then $x_{k+1}$ will be much close.($x^*=argminF(x)$). It says the error is squared at every step, so if we're converging to a limit, it will be 3.

That's Newton's method for equations, now we want to do Newton's method for **optimization**—— $minimize \ \ F(x)$. so what's the connection between them? Minimize $F(x)$ corresponds to solving $\nabla F =0$.

# Optimization

Two methods:

1. **Steepest descent**:
   $$
   x_{k+1}=x_k-s_k\nabla F
   $$
   s is *step size*, it's often called *learning rate* in deep learning.

   The rate of convergence for steepest descent is linear. The error is multiplied at every step by some constant below 1.

2. **Newton's method**:
   $$
   x_{k+1}=x_k-H^{-1}\nabla F
   $$
   Notice that the $J$ in equation (4) is $H$.

   The convergence rate for Newton's method is quadratic, that means super fast convergence if you start close enough.

# Convexity

**Convex minimization:** minimize a convex function for points in a convex set

## Convex Set

$K$ is a convex set, if $x$ and $y$ are in $K$, so is the line from $x$ to $y$ 

Union of convex sets is usually not convex, intersection of convex sets is always convex.

## Convex Function

$F$ is a convex function, if the set of points on and above the graph of $F$ are convex set.

***How to test?***

1. **one function of one variable** 

   $f(x)$ is convex if $\frac {d^2f}{dx^2}\geq0$.

2. **n functions of n variables**

   Hessian matrix $H$ is positive semidefinite.

   
