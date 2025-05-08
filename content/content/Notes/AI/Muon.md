paper: [https://arxiv.org/pdf/2409.20325](https://arxiv.org/pdf/2409.20325)

## Linear Algebra Background

The trace is invariant under circular shifts.

$tr(ABC) = tr(CAB) = tr(BCA) = \sum_i \sum_j \sum_k a_{ik}b_{kj}c_{ji}$

### Dual Norms

This helps us understand the Frobenius norm of matrix $A=U\Lambda V^T$

$||A||^2_F = tr(AA^T) = tr(U \Lambda V^T V \Lambda^T U^T) = tr(U \Lambda^2 U^T) = tr( U^T U \Lambda^2) = tr(\Lambda^2)$

Which shows that $||A||_F = \sum_i \lambda_i^2$

Now the dual norm is defined as

$||y||_* = \sup_{||x|| \leq 1} y \cdot x$

For frobenius norm this means

$||A||_{F*} = \sup_{||B|| \leq 1} tr(AB^T)$

Suppose $A, B \in \mathbb{R}^{m \times n}$, $m < n$.

Intuitively, if $A=U\Lambda V^T$, we can set $B=\frac{1}{\sqrt{tr(\Lambda^2)}}U\Lambda V^T$

### SVD

What is the proof that the SVD exists?

The key insight is that we want to _symmetrize_ the matrix.

Suppose $A \in R^{m \times n}$, then $A^TA$ is symmetric.

Is is also positive semidefinite. This means $x^TA^TAx = ||x||^2\geq 0$, which means that the eigenvalues are real and positive. It can have repeated eigenvalues and eigenvalues of $0$, which means that it is not full rank. But it must be decomposable into $A^TA = U\Lambda U^T$, where $\Lambda$ is real and positive.

Now suppose $Au_i = v_i$, for some basis vector $u_i \in U$. Then $A^Tv_i = u_i$.

These $v_i$ must be orthogonal because $u_j^TA^TA u_i = u_j^T \lambda_i u_i = 0 = v_j^T v_i$.

In SVD, the eingenvalues are real and positive.

### Steepest Descent

$\text{arg min}_w g^Tw + \frac{\lambda}{2}||w||^2$ 

Apparently we can understand this through the dual operator norm.

Through linearity, we know that $||aw|| = a||w||,$ where a is a scalar, and

Thus, we must have that the direction of $w$ is $\text{arg max}_{||t|| = 1} g^T t$.  

Then, we simply need to choose the $a$ that maximizes $a \max_{||t|| = 1} g^T t + \frac{\lambda a^2}{2}$

$||g||^\dagger = \max_{||t|| = 1} g^T t$ (the dual norm), so we get that $a = \frac{-||g||^\dagger}{\lambda}$.

This is how proposition 1 is derived.

### An optimization problem

Consider

$\text{arg min}_A{||G-A||_F}$ , subject to $AA^T = I$ or $A^TA = I$ (A is semi-orthogonal).

$||G - A||_F = tr(GG^T - AG^T - GA^T + AA^T)$

So the problem simpilfies to

$\text{arg max}_A {tr(G A^T)}$

WLOG, suppose $G \in R^{m \times n}$, where $m < n$. Then $AA^T = I$.

Let $G=U\Lambda V^T$, and assume $V$ is full rank.

Then this becomes

$\text{arg max}_{a_i} tr(\sum \lambda_i u_i a_i^T)$ s.t. $a_i^Ta_i = 1$

It just so happens that you want to set $a_i = u_i$

You can also see this through the cyclic trace property

(should add a derivation here)

## Results

Adam, without EMA, is sign gradient descent.

**Sign descent as steepest descent under infinity norm**

When the norm is $||..||_\infty$, then $w = \frac{||g||_1}{\lambda}\text{sgn}(g)$ 