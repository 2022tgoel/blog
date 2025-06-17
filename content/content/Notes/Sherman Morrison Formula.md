
For in-context learning, you have the following minimization problem 

$L_t(\Phi) = \frac{1}{2} ||(V_t - \Phi K_t )||^2$ , $V_t, K_t \in \mathbb{R}^{d \times T}, \Phi \in \mathbb{R}^{d \times d}$ 

you can also add a regularization term 

$L_t(\Phi) = \frac{1}{2} ||(V_t - \Phi K_t)||^2 + \frac{1}{2 \lambda} ||\Phi||^2$  

Which has the regular least squares solution 

$\nabla L = (V_t - \Phi K_t) K_t^T - \frac{1}{2 \lambda} \Phi= 0$

$\Phi = (V_t K_t^T)(K_tK_t^T + \frac{1} {\lambda} I)^{-1}$ 

Basically the inverse is super annoying, but it kind of helps that the matrix that you are inverting is only receiving a low-rank update $A \rightarrow A + k_t k_t^T$ 

$(A + uv^T)^{-1} = A^{-1} + \frac{A^{-1} u v^T A^{-1}}{1 + v^T A^{-1} u}$ 

$\begin{align}(A^{-1} - \frac{A^{-1} u v^T A^{-1}}{1 + v^T A^{-1} u}) (A + u v^T) \\ &= (I + A^{-1} u v^T - \frac{A^{-1} u v^T + A^{-1} u v^T A^{-1} u v^T}{1 + v^T A^{-1} u}) \\ &= (I + A^{-1} u v^T - \frac{A^{-1} u v^T + A^{-1} u v^T A^{-1} u v^T}{1 + v^T A^{-1} u}) \\ &= (I + A^{-1} u v^T - \frac{ A^{-1} u (1 + v^T A^{-1} u) v^T }{1 + v^T A^{-1} u}) \\ &= I \end{align}$ 


