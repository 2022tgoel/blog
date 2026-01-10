
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