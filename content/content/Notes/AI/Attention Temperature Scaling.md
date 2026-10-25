
## View #1 Simple

$\Delta = z_{\text{signal}} - z_{\text{noise}}$  . Then $p_\text{signal} = \frac{1}{1 + Ne^{-\Delta}}$, so it washes out as you scale $N$. Then, scaling the logits by $\lambda = \frac{\log{N / \alpha}}{\Delta}$  makes it  so that $p_\text{signal} = \frac{1}{1 + \alpha}$. 

You need to know what delta is 🧐

Also, you are assuming that the $\Delta$ is constant, you might expect that if you are sampling the noise logits from normals that the gap between the signal and the top noise logit will decrease over time. 

## View #2: Matching Entropy

Logits: $z_i$, partition function $Z = \log{\sum \exp{z_i}}$, $E[Z] \leq n \sqrt{e}$ , 

Entropy
$$
\begin{aligned}
S = Z - \sum p_i z_i 
\end{aligned}
$$

## View #3 

$$
\begin{aligned}
&E [\max{z_i}] \leq \frac{1}{\lambda}\log E[e^{\lambda \max{z_i}}] \leq \frac{1}{\lambda} \log \sum E[e^{\lambda z_i}] = \frac{1}{\lambda} \log {n e^{\frac{\lambda^2}{2}}} = \frac{\log{n}}{\lambda} + \frac{\lambda}{2} = 2 \frac{\sqrt {\log n} }{\sqrt{2}} = \sqrt{2 \log n}   
\\
&-\frac{\log{n}}{\lambda^2} + \frac{1}{2} = 0 \implies \lambda = \sqrt{2 \log n}
\end{aligned}
$$
$E[\sum e^{\lambda z_i}] = n e^{\frac{\lambda^2}{2}}$ 


https://nor-blog.pages.dev/posts/2025-11-27-attention-and-long-context/

