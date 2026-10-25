
https://arxiv.org/abs/2602.01480

Suppose you have typical GD
$$ \begin{align} w_{t+1} = w_t + \nabla L(w_t) \end{align} $$

Then we can define the central flow 

$$ \begin{aligned} \bar{w}_t &= \frac{w_t + w_{t+1}}{2} 
\\
\delta_t &= \frac{\eta}{2}\nabla L(w_t) \end{aligned}  $$
Then we can define the updates for the central flow and the covariance matrix of the oscillation $\Sigma = \delta_t \delta_t^T$ 

$$
\begin{aligned}
\frac{d \bar{w}_t}{dt} &= \frac{\eta}{2} (\nabla L(w_t) + \nabla L(w_{t-1}))
\\
\frac{d \Sigma}{dt} &=  \frac{\eta^2}{4}(\nabla L(w_t)\nabla L(w_t)^T + \nabla L(w_{t-1})L(w_{t-1})^T) - 2 \Sigma
\end{aligned}
$$

### Backwards error correction

If you have a continuous function that the discretized version will have some error and vice versa. As a simple example, consider the continuous ODE $\frac{dx}{dt} = \lambda x$. The continuous form is $x(t) = x(0) e^{\lambda t}$ , and the discretized form is $x_t = (1 + \lambda \Delta t)x_{t-1} \implies x(t) = (1 + \lambda \Delta t)^{\frac{t}{ \Delta t}} x(0)$. Now in the limit this version does approach the continuous form, but in practice there is some real error. 

If we have a continous ODE with $\tilde{V}(x) = \frac{dx}{dt}$, then 

$$
\Delta x \approx \tilde{V}(x) \Delta t + \frac{\Delta t^2}{2} \nabla \tilde{V} \tilde{V} 
$$ which should be made to equal 
$$
V(x) \Delta t
$$ 
Thus, the appropriate choice for $\tilde{V}$ to make a second order correction is $V - \frac{\Delta t}{2} \nabla V V$

Thus, the refined form is 

$$
\begin{aligned}
\frac{d \bar{w}_t}{dt} &= \frac{\eta}{2} (\nabla L(w_t) + \nabla L(w_{t-1})) - \frac{\eta^2}{4}(\nabla^2 L(w_t) + \nabla^2 L(w_{t-1}))(\nabla L(w_t) + \nabla L(w_{t-1}))
\end{aligned}
$$

https://eregis.github.io/blog/ 

## Examples

### Flat Landscape

$$
\begin{aligned}
&L(w) = -\beta w \\
&\frac{d\bar{w}}{dt} = -\beta \eta \\
&\frac{d\Sigma}{dt} = \frac{\eta^2}{2}\beta^2 - 2 \Sigma\\
&\Sigma = \frac{\eta^2\beta^2}{4}\\
&\bar{w} = -\beta \eta t
\end{aligned}
$$

### Quadratic

$$
\begin{aligned}
&L(w) = \frac{1}{2}\beta w^2\\
&\frac{d\bar{w}}{dt} = \left(\frac{\eta}{2}\beta -  \frac{\eta^2\beta^2}{2}\right) (w_t + w_{t-1}) =  \left(\eta\beta -  \eta^2\beta^2\right) \bar{w}_t \\
&\frac{d\Sigma}{dt} = \frac{\eta^2\beta^2}{4}(w_t^2 + w_{t-1}^2) - 2 \Sigma
\end{aligned}
$$
With $\bar{w}(0) = 0$, then $\bar{w}(t) = 0$, so then $w_t = \delta_t$, so then $w_t^2 + w_{t-1}^2 = 2 \Sigma$, so 

$$
\begin{aligned}
\frac{d\Sigma}{dt} = \left(\frac{\eta^2\beta^2}{2} - 2 \right)\Sigma
\end{aligned}
$$
so as long as $\eta \leq \frac{2}{\beta}$ the variance shrinks, getting the expected relationship. 
### Quartic
$$
\begin{aligned}
&L(w) = \frac{S}{2} w^2 - \frac{Q}{4} w^4\\
&\frac{d\bar{w}}{dt} = 
\\
&\frac{d\Sigma}{dt} = \frac{\eta^2}{4}\left((Sw_t - Qw_t^3)^2 +(Sw_{t-1} - Qw_{t-1}^3)^2 \right) - 2 \Sigma
\end{aligned}
$$