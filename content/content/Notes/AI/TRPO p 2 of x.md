
see: [[TRPO p 1 of x]]

> The first proof extends Kakade and Langford’s result using the fact that the random variables from two distributions with total variation divergence less than $\alpha$ can be coupled, so that they are equal with probability $1-\alpha$. The second proof uses perturbation theory.

### Coupling
https://maths.dur.ac.uk/stats/courses/StochProc34/1516Coupling34.pdf
Suppose you have two starting distributions on a Markov chain $P$, denoted as $\pi$ and $\lambda$.

$x_n \sim P^n\pi$, $y_n \sim P^n \lambda$

We can define a coupling distribution on $x_n$ and $y_n$, than basically says that $x_n$ and $y_n$ move to the same state once they hit the same point. If $T$ is the first time step where $x_n = y_n$, then $\forall n \geq T, x_n = y_n$

Why is considering such a coupling useful? 
Well it helps us bound the total variation distance between $P^n \pi$ and $P^n \lambda$

$d_{TV} (P^n \lambda, P^n \pi) \leq P(T > n)$ -- places where they have converged in the coupled distribution correspond to no variation distance

Another way to think of this is in the reverse direction:
$P(T \leq n)\leq 1 - d_{TV}(P^n \lambda, P^n \pi)$ 

**Maximal Coupling**

You can construct a coupling (joint distribution) such that the states are equal with probability $1 - d_{TV}(\lambda, \pi)$ and the marginals are $\lambda$ and $\pi$ 

$P(x=y=s)= \min{(\lambda(s), \pi(s))}$ 

$P(x=s, y=s') = \frac{[\lambda(s) - \min{(\lambda(s), \pi(s))}] [\pi(s') - \min{(\lambda(s'), \pi(s'))}]}{d_{TV}(\lambda, \pi))}$ , where $s \neq s'$

useful fact: $1 = d_{TV}(\lambda, \pi) + \sum \min(\lambda(s), \pi(s))$ 

$\frac{[\lambda(s) - \min{(\lambda(s), \pi(s))}] [\pi(s') - \min{(\lambda(s'), \pi(s'))}]}{d_{TV}(\lambda, \pi))}|_{s=s'} = 0$

This means $\sum_{s\neq s'} P(x=s, y=s') = \sum_{s, s'} \frac{[\lambda(s) - \min{(\lambda(s), \pi(s))}] [\pi(s') - \min{(\lambda(s'), \pi(s'))}]}{d_{TV}(\lambda, \pi))} = d_{TV}(\lambda, \pi)$ 

## Proof
Suppose you are in the same state $s$ and then sample under the maximal coupling for $\pi$ and $\lambda$ 
With probability $1 - d_{TV} (\pi, \lambda)$ you get the same action. In this case, the probability distribution from the next state $s'$ is the same. If you don't get the same action, than let's say the states can diverge by an unbounded amount, with total variation up to 1. The total variation of the distributions over the next state is still $1 - d_{TV} (\pi, \lambda)$.

This shows that  $\eta(\pi^*) - L_\pi(|pi^*) = \sum_s (p_{\pi^*} (s) - p_{\pi} (s)) \sum_a \pi^* (a | s) A(s, a) \leq \frac{2 \epsilon}{1 - \lambda}$    

https://spinningup.openai.com/en/latest/spinningup/exercises.html
This seems like potentially a fun thing to do.

## Policy Gradient Theorem

$J(\theta) = E_{\pi_\theta} [R]$ where the expectation is under the stationary distribution $d^\pi$
$\nabla_\theta J(\theta) = E_{\pi_\theta} [\nabla_\theta \log{\pi_\theta (a | s) Q^{\pi_\theta}(s, a)}]$

$J(\theta) = \sum_s d_{\pi_\theta} (s) R(s)$ 

$\nabla V(s) = \nabla \sum_{a} \pi(a |s) Q(s, a) = \sum_{a} Q(s, a) \nabla \pi(a | s) + \pi(a | s) \nabla Q(s, a)$ 

$\nabla Q(s, a) = \nabla [r(s) + \gamma \sum_{s'} P(s' | s, a) V(s')] =  \gamma \sum_{s'} P(s' | s, a) \nabla V(s')$  

Thus,
$\nabla V(s) = \sum_{s', a'} p_\pi (s') \nabla \pi(a | s') Q(s', a)$ where $p_\pi$ is the discounted visitation probability

