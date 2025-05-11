[[TRPO p 1 of x]]: I think this is pretty wrong now

[[TRPO p 2 of x]]

After a bunch of simplification, we arrive at the objective

$L(\theta) = E_{s \sim p_\pi, a \sim \pi} [\frac{\pi_\theta(a | s)}{\pi(a | s)} Q(s, a)]$

$\max_\theta L(\theta)$ 

subject to 

$E_{s \sim p_\pi} [D_{KL}(\pi || \pi_{\theta})] \leq \delta$ 

First, we want to simplify the KL-divergence that we are dealing with. 

$\nabla_\theta D_{KL}(\pi ( \cdot | s ) || \pi_{\theta} ( \cdot | s )) = \nabla_\theta \sum_a \pi (a | s) \log{\frac{\pi (a | s)}{\pi_\theta (a | s)}} = \sum_a -\frac{\pi(a | s)}{\pi_\theta (a | s)} \nabla_\theta \pi_\theta (a | s)$ 

If this is evaluated at $\pi_\theta = \pi$, then it is $\sum_a - \nabla_\theta \pi_\theta (a | s) = 0$ 

Let's move to the second derivative. 

$\nabla^2_\theta D_{KL}(\pi ( \cdot | s ) = \nabla_\theta \sum_a  -\frac{\pi(a | s)}{\pi_\theta (a | s)} \nabla_\theta \pi_\theta (a | s) = \sum_a \frac{\pi (a | s)}{\pi_\theta^2(a | s)} (\nabla_\theta \pi_\theta (a | s))^2 - \frac{\pi (a | s)}{\pi_\theta(a | s)} (\nabla^2_\theta \pi_\theta (a | s))$  

If we evaluate this again at $\pi_\theta = \pi$, we get 

$\nabla^2_\theta D_{KL}(\pi ( \cdot | s ) = \sum_a \pi (a | s) (\frac{\nabla_\theta \pi_\theta (a | s)}{\pi (a | s)})^2$  which is the fisher information matrix, which I will refer to as $A$

By Lagrange multipliers, we want to choose the direction such that 

$E_{s \sim p_\pi}[A] \Delta \theta = g$, where $g$ is $\nabla_\theta L(\theta) = E_{s \sim p_\pi, a \sim \pi} [\frac{\nabla_\theta \pi_\theta(a | s)}{\pi(a | s)} Q(s, a)] = \nabla_\theta E_{s \sim p_\pi, a \sim \pi} [\log \pi_\theta(a | s) Q(s, a)]$   

A key fact is that the fisher information matrix is symmetric, since it's a Jacobian. Thus, we know that all of the eigenvectors are orthogonal, and can apply conjugate gradient descent. 

How to multiply by the fisher information matrix efficiently:


