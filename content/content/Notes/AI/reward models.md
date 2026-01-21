
Any kind of *learned* backprop/compression strategy can also be viewed as as backprop under a reward model. In a sense, reward models and learned compression are two sides of the same coin: *learning how to learn*. 

For example, we all know that delta net is backprop. 

$L(M, k, v) = \frac{1}{2}||Mk - v||_2^2$ 

Then $M = M - \eta \nabla L \implies M = M - \eta (Mk - v) k^T = M(I - \eta k k^T) + \eta v k^T$ .

Now, gated delta net adds a scalar decay term. Learning this decay term empirically helps a lot. You can say that it helps because it gives the model the inductive bias to forget, which is true. It also gives the model to control its learning behavior.

$M = M {\color{red} \alpha} (I - \eta k k^T) + \eta v k^T = M - (1 - \alpha)M - \eta (\alpha Mk - v) k^T$  

which is an update you would get under the loss function

$L(M, k, v) = \frac{1}{2} ((1 - \alpha) ||M||_F^2 + \frac{\eta}{\alpha}||\alpha Mk - v||_2^2)$  

Admittedly, this isn't the cleanest expression. But it does show that we are giving the model the ability to assign penalties to remembering and modulate how large this penalty is through $\alpha$. 

Something about forgetting doesn't feel quite right to me. I feel like forgetting should be a *side effect*, rather than a *feature*, of compression. Realistically information compression in context of DL is going to be a bit lossy, but we still hope we can remember everything. The fact that it is encouraged in every linear attention architecture variant seems a bit strange. But this goes into a separate topic of whether regularization is a sensible loss term or an artifact of deeper problems. The main point is that I do think that working towards richer, denser reward signals is going to be very important, and can also be framed at the problem of the model knowing how to update itself and continually learn (as in, the way we get there might not actually look like having a reward model). 

https://arxiv.org/pdf/2211.15661

https://arxiv.org/pdf/2304.08467