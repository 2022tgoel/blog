
Supposed you have a single-index gaussian model. $X$ is your feature, $Z = w^* X$ is the latent, $P(Y | Z) = I_{Y = \sigma(Z)}$ is the distribution of the output given the latent (in this case it is a deterministic mapping to $\sigma(Z)$, and you are trying to estimate $w^*$ 

A simple thing is to see that $E[XY] = w^* E[Z \sigma(Z)]$. so as long as $E[Z \sigma(Z)] \neq 0$ (e.g. $\sigma$ is increasing, then you are able to estimate $w^*$ this way)

The variance of this estimator is $Var[XY] = E[w^2 Z^2 \sigma(Z)^2 + G_\perp^2 \sigma(Z)^2] - w^2(E[Z \sigma(Z)])^2 = ||w^\star||^2Var[Z \sigma(Z)] + E[\sigma(Z)^2] (d-1)$ 
so you need $\Theta(d)$ samples so get $||w^\star - w||^2 = O(\epsilon)$ 

Now we are going to prove some bounds for normal SGD

### Hermite Polynomials

It's going to be useful to decompose the function $\sigma$ into some a sum of hermite polynomials, so let's talk about what they are $\sigma(X) = \sum a_j h_j(x)$ 

$$\boxed{ H_n(x)=(-1)^n e^{x^2/2} \frac{d^n}{dx^n}e^{-x^2/2} } $$

$H_0(x) = 1, H_1(x) = x, H_2(x) = x^2 - 1$ 

$L = E\left[||\sigma(w X) - \sigma(w^\star X)||^2\right]$
Now they have the useful property that $E[h_j(wX) h_l(w^\star X)] = I_{j = l} m^j$, where $m = w^\star w^T$ 

### SGD 
If you pin $||w|| = ||w^\star|| = 1$ (radial projection of the gradient), then the update direction of steepest descent is $\frac{\partial L }{\partial w} = \frac{\partial L}{\partial m} \frac{\partial m}{\partial w} = a_k k m^{k-1} (w^* - m w)$ , If $m^2$ is small then $\delta m \approx  \eta a_k k m^{k-1}$

$n \approx \int_{m_0}^b \frac{1}{\eta a_k k m^{k-1}} dm$