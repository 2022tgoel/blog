
Here, we are going to derive some of the key principles in the theory of feature learning. 

We know that the condition $||W||_* = \Theta\left(\sqrt{\frac{n_{l}}{n_{l-1}}}\right)$  and $||\Delta W||_* = \Theta\left(\sqrt{\frac{n_{l}}{n_{l-1}}}\right)$ is sufficient for feature learning, because of the alignment between the gradient update and the hidden state. 

In the case of many tokens, many batches, and many timesteps, assuming assuming there is a single rank-$1$ matrices still having the $\Theta\left(\sqrt{\frac{n_{l}}{n_{l-1}}}\right)$ scaling, then you are averaging over large constant ($B$, number of batches, $t$, number of timesteps, etc), which still gives you the same asymptotic scaling. 

Stable rank = $\frac{\sum_i \sigma_i^2}{\max_i \sigma_i^2}$

|            | Stable Rank          | Spectral Norm                  | Frobenius Norm                                    | RMS                                           |
| ---------- | -------------------- | ------------------------------ | ------------------------------------------------- | --------------------------------------------- |
| $W$        | $\min(n_l, n_{l-1})$ | $\sqrt{\frac{n_{l}}{n_{l-1}}}$ | $\sqrt{\frac{\min(n_l, n_{l}) * n_{l}}{n_{l-1}}}$ | $\sqrt{\frac{\min(n_l, n_{l-1})}{n_{l-1}^2}}$ |
| $\Delta W$ | $1$                  | $\sqrt{\frac{n_{l}}{n_{l-1}}}$ | $\sqrt{\frac{n_{l}}{n_{l-1}}}$                    | $\sqrt{\frac{1}{n_{l-1}^2}}$                  |

Now we want to derive these two central scaling rules

$$
\begin{aligned}
\sigma_l &= \Theta \left(\sqrt{\frac{\min(n_l, n_{l-1})}{n_{l-1}^2}}\right) = \Theta \left(\sqrt{\frac{1}{n_{l-1}}}\min\left(1, \sqrt{\frac{n_l}{n_{l-1}}}\right)\right)  \\
\eta_l &= \Theta \left(\frac{n_l}{n_{l-1}}\right)
\end{aligned}
$$

Seeing the weight init constraint is easy, we just want the RMS to match.

For the learning rates, we know that $||\nabla_{W} L||_* = ||\nabla_{h_{l-1}} L||_2 ||h_{l-1}||_2$ and $||h_{l-1}||_2 = \Theta \left( \sqrt{n_{l-1}}\right)$ 

And then $||\nabla_{h_{l-1}} L||_2 = \Theta \left( \frac{1}{\sqrt{n_l}}\right)$. We can derive this through layerwise recursive analysis. 

$||\nabla_{h_{l-1}} L||_2 = ||W^T \nabla_{h_{l}} L||_2 = \Theta\left(\frac{\sqrt{n_l}}{\sqrt{n_{l-1}}} \frac{1}{\sqrt{n_{l}}}\right) = \Theta\left(\frac{1}{\sqrt{n_{l-1}}} \right)$

Ok so it obeys the recurrence. And then what about the base case? Well let's just say that $L = ||h_L||^2$ (a kind of reasonable loss function). Then $\nabla_{x_L} L = \Theta\left(h_L\right)$. This seems bad, but I think what you can say is that $h_L \in \mathbb{R}^1$, so $\sqrt{n_L} = \frac{1}{\sqrt{n_{l-1}}} = 1$ 

There are a lot of hidden assumptions in all of this analysis (e.g. things never cancel out each other exactly, which is what allows you to say $\Theta(x + y) = \Theta(x) + \Theta(y)$). However, the one I think is strange is that you kind of assume that $n_l \geq n_{l-1}$ when saying that the hidden vector will lie in the subspace created by the randomly initialized matrix. Like, what if this doesn't happen? 

## Lazy and rich training regimes

### Notation

$f(n) = O(g(n)) \implies \limsup \frac{f(n)}{g(n)} \leq c$ for some constant c 
$f(n) = \Omega(g(n)) \implies \limsup \frac{g(n)}{f(n)} \leq c$ for some constant c 
$f(n) = o(g(n)) \implies \lim \frac{f(n)}{g(n)} = 0$ 
$f(n) = \omega(g(n)) \implies \lim \frac{g(n)}{f(n)} = 0$ 
### Analysis


Suppose you have the model 

$h_3(h_0) = g_3 W_3 g_2 W_2 g_1 W_1 h_0$ 

The $g$'s are going to be be another way of expressing the learning rate 

$\Delta h_l = g_l\underbrace{\Delta W_l h_{l-1}}_{layer} + g_l\underbrace{W_l \Delta h_{l-1}}_{passthrough}$

$\Delta W_l = g_l\frac{\partial L}{\partial h_{l}} h_{l-1}$ 

So the layer term is

$g_l^2 \frac{\partial L}{\partial h_{l}} ||h_{l-1}||^2$ 

The passthrough term is 

$$
\begin{align}
g_l W_l \Delta h_{l-1} &= g_l g_{l-1} W_l \Delta W_{l-1} h_{l-2} + g_l g_{l-1} W_l W_{l-1} \Delta h_{l-2} \\
&\approx g_l g_{l-1}^2 W_l \frac{\partial L}{\partial h_{l-1}} ||h_{l-2}||^2 \\
&= g_l^2 g_{l-1}^2 W_l W_l^T \frac{\partial L}{\partial h_l} ||h_{l-2}||^2 
\end{align}
$$
**We ignore the other passthrough terms**, though the justification not clear to me. I think it might be more of a fair assumption near initialization, because the weights and representation updates are less likely to be meaningfully aligned. 


**This makes the major assumption that $W_l$ is independent of $\frac{\partial L}{\partial h_l}$, which is not super obvious**:

Also assume $g_l^2 \sigma_l^2 n_{l-1} \sim 1$ 

$$
\begin{align}
\frac{\partial L}{\partial h_l}^T \Delta h_l &= g_l^2 \left|\left|\frac{\partial L}{\partial h_{l}}\right|\right|^2 ||h_{l-1}||^2 + g_l^2 g_{l-1}^2 \left|\left|W_l^T \frac{\partial L}{\partial h_{l}}\right|\right|^2 ||h_{l-2}||^2 \\

&= g_l^2 \left|\left|\frac{\partial L}{\partial h_{l}}\right|\right|^2 ||h_{l-1}||^2 + g_l^2 g_{l-1}^2 \sigma_l^2 n_{l-1} \left|\left|\frac{\partial L}{\partial h_{l}}\right|\right|^2 ||h_{l-2}||^2 

\end{align}
$$



