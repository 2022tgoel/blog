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

Now suppose $Au_i = \alpha_i v_i$, for some basis vector $u_i \in U$ and some other normalized basis vector $v_i$.

1. These $v_i$ must be orthogonal because $u_j^TA^TA u_i = u_j^T \lambda_i u_i = 0 = \alpha_i \alpha_j v_j^T v_i$.
2. $\alpha_i = \sqrt{\lambda_i}$, because $u_i^T A^T A u_i = \lambda_i = \alpha_i^2 v_i^T v_i$
3. $A^T \sqrt{\lambda_i} v_i = \lambda_i u_i$.

In SVD, the eigenvalues are real and positive.

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

## Resources

https://fdangel.com/posts/kfac_explained.html

https://kvfrans.com/matrix-whitening/

https://lucasjanson.fas.harvard.edu/papers/A_New_Perspective_On_Shampoos_Preconditioner-Morwani_ea-2024.pdf

[Central Flows](https://arxiv.org/pdf/2410.24206)

https://www.cs.toronto.edu/~jmartens/docs/HF_book_chapter.pdf

https://indrag49.github.io/Numerical-Optimization/conjugate-gradient-methods-1.html

https://arxiv.org/pdf/2507.12224

## Nesterov Momemtum

$$
\begin{aligned}
&v_{t+1} = \mu v_t - \nabla f(\theta_t + \mu v_t)\\
&\theta_{t+1} = \theta_t + v_{t+1}
\end{aligned}
$$

Now suppose you are at $\theta = \theta_t + \mu v_t$ and have calculated $g$ through backpropogation. If you want to finish the update,

$$
\begin{aligned}
\theta_{t+1} &= \theta - g \\
v_{t+1} &= \mu v_t - g \\
\theta_{t+1} + \mu v_{t+1} &= \theta - g + \mu v_{t+1} \\
&= \theta + \mu^2 v_t - (1 + \mu) g
\end{aligned}
$$

Note that the scale is $\frac{1 + \mu}{1-\mu^2} = \frac{1}{1 - \mu}$, so you have the same long-horizon scale factor.

## GGN Approximation

Motivation: MSE: $L(x) = \sum (y_n - f(x_n, \theta))^2$

Different terms related to loss. Really important to get this right!

* Unnormalized logits
* Normalized logits (what you get after applying a `log_softmax`)
* CrossEntropy loss: multiplying by the class labels
* NLL Loss

If you have a function $L(f(x), y)$

$$
H_x \approx (J_xf) ^T H_f (J_xf)
$$

with $f \in \mathbb{R}^n, x \in \mathbb{R}^m$, then $H_f \in \mathbb{R}^{n \times n}, J_xf \in \mathbb{R}^{n \times m}$

In the case of the cross entropy loss function, where $f$ are the unnormalized logits, $f^n$, are the normalized logits, and $c$ is the true class,

NLLLoss: $\langle y, f^n\rangle$
CrossEntropyLoss: $\langle y, \text{log softmax}(f) \rangle$

$$
\begin{align*}
L &= -\sum y_i \log{p_i} \\
J_f &= p - y\\
H_f &= \text{diag}(p) - p p^T
\end{align*}
$$
So $J_f$ being small is what makes this a good approximation (think of the MSE motivation). 

This is where the distinction between empirical fisher and fisher become important!! 

So $H_f = E \left[ J_f J_f^T \right] = p p^T - pE[y]^T - E[y] p^T + E[y y^T] = \text{diag(p)} - p p^T$, where the expectation is over $p$ and the jacobians are for every token (the actual fisher), it's not at all clearly related to this "empirical fisher" stuff. https://arxiv.org/pdf/1905.12558.  

Additionally

$$
\begin{align*}
J_xL = (p - y) J_xf
\end{align*}
$$
So if

$$
\begin{align*}
H_x &\approx (J_xf) ^T (\text{diag}(p) - p p^T) (J_xf)\\

\text{reshape}(H) &= \sum_i p_i (G_i \otimes G_i) - \left(\sum_i p_i G_i\right) \otimes \left(\sum_i p_i G_i\right)
\end{align*}
$$
https://proceedings.neurips.cc/paper_files/paper/2024/file/350e718ff74062b4bac2c6ffd9e1ac66-Paper-Conference.pdf
## Fisher Information

If you use fisher instead of the hessian, then coordinate transformations are exactly the same

Transform: $f(\theta) \rightarrow \phi$

step $F^{-1} g$ or $H^{-1} g$


$F(\theta) = E\left[ \nabla_\theta \log p(x | \theta) (\nabla_\theta \log p(x | \theta) )^T \right]$

$F(\phi) = E\left[ \frac{\partial \theta}{\partial \phi}^T \nabla_\theta \log p(x | \theta) (\nabla_\theta \log p(x | \theta) )^T \frac{\partial \theta}{\partial \phi} \right] = \frac{\partial \theta}{\partial \phi}^T F(\theta) \frac{\partial \theta}{\partial \phi}$


the relationship is actually even deeper than this.

$F(\theta) = E\left[ \nabla_\theta \log p(x | \theta) (\nabla_\theta \log p(x | \theta) )^T \right] = E\left[ \frac{1}{p(x | \theta)^2} \nabla_\theta p(x | \theta) \nabla_\theta p(x | \theta)^T \right]$

$E\left[-\nabla_\theta^2 \log_\theta p(x) \right]$

## Reading List

https://arxiv.org/pdf/2505.21799

https://arxiv.org/pdf/2509.26030

---
https://arxiv.org/pdf/2110.01765

https://main-horse.github.io/translations/nccl/

https://proceedings.neurips.cc/paper_files/paper/2024/file/986292a930c3692168b177a770025ab3-Paper-Conference.pdf

https://arxiv.org/abs/1711.04735