This is my derivation of equation 6 in [https://arxiv.org/pdf/1502.05477](https://arxiv.org/pdf/1502.05477)

Two key facts:

$\sum_a \pi(a|s) A_\pi(s, a) = 0$ because $\sum_a \pi(a | s) Q_\pi(a, s) = V_\pi(a, s)$ 

Additionally
$\nabla \pi^*(a | s) = \pi'(a | s) - \pi_{old}(a|s)$

$\sum_s \nabla^2 \pi^* = 0$

$\nabla^2 \eta (\pi^*) = 2 \sum_{s'} \sum_{a'} p_{\pi^*} (s') \nabla \pi^*(a' | s')\gamma \sum_s p_{\pi^*}(s |s', a') \sum_a \nabla \pi^*(a | s) A_\pi(s, a)$    

Thus,

$|\sum_a \nabla \pi^*(a | s) A_\pi(s, a)| = |\sum_a \pi'(a | s)A_\pi(s, a) - \pi(a|s)A_\pi(s, a)| = |\sum_a \pi'(a | s)A_\pi(s, a)| \leq \epsilon$

where epsilon is defined in the paper

Thus,

$|\nabla^2 \eta(\pi^*)| \leq 2 \sum_{s'}\sum_{a'} p_{\pi^*} (s') |\nabla \pi^*(a' | s')|\gamma \sum_s p_{\pi^*}(s |s', a') \epsilon = 2 \sum_{s'}\sum_{a'} p_{\pi^*} (s') |\nabla \pi^*(a' | s')| \frac{\epsilon\gamma}{1 - \gamma}$ 

$\sum_{a'} |\nabla \pi^*(a' | s')|$ is the total variation distance between the two distributions, which is bounded by 2.

Thus, the final bound is

$|\nabla^2 n(\pi^*)| \leq \frac{4 \epsilon \gamma}{(1 - \gamma)^2}$

Then, you multiply by $\frac{\alpha^2}{2}$, which is the integration region

(we are using peano’s integration formula, basically a taylor expansion thing)

There are also other terms that presumably become 0 that I just ignored. 