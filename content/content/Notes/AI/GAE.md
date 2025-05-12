https://arxiv.org/pdf/1506.02438

In this paper, the setting is that we want to develop lower variance estimates of the undiscounted reward function

$V^\pi(s) = E_{s \sim p_\pi} [\sum_{t=0}^\infty r_t]$ 

**Bias variance tradeoff**

You have an estimator $\hat{f}$ of something

$E[(\hat{f} - E[f])^2] = (E[\hat{f}] - E[f])^2 + Var(\hat{f})$ 

In this scenario, we have

$E[f] = V^\pi(s)$. We would like to know exactly how good it is to be in this state. 

$\hat{f}$ is our regular estimator $\sum r_t$ (sum of rewards along a particular trajectory). 

$\hat{f}$ is an unbiased estimator, but it is also high-variance. 

In general, our approach will be to reduce variance by introduction to bias. One first step is the introduction of the discount factor $\gamma$. 

Our new estimator is  $\sum \gamma^t r_t$, which reduces bias by reducing the impact of terms where $t >> 1/(1-\gamma)$. 

Let's say we had access an approximate value function $V \approx V^\pi$. Then, we could really reduce the variance of the function, and make our estimator $r_t + \gamma V(s_{t+1}) - V(s_t)$. This can only take a number of distinct values equal to the magnitude of the state space. But it also puts a of faith in $V$ being an accurate approximation. 

There are middle grounds. 

Let $\delta_t^V = r_t + \gamma V(s_{t+1}) - V(s_t)$ 

$\delta_t^V + \gamma \delta_{t+1}^V = -V(s_t) + r_t + \gamma r_{t+1} + \gamma^2 V(s_{t+2})$ 

$\delta_t^V + \gamma \delta_{t+1}^V + \gamma^2 \delta_{t+2}^V  = -V(s_t) + r_t + \gamma r_{t+1} + \gamma^2 r_{t+2} + \gamma^3 V(s_{t+2})$ 

Add you add more terms, you reduce the bias, and introduce more variance, really highlighting the tradeoff. 

The approach that the paper takes is a more steeply discounted sum of the bellman residuals terms ($\delta_t^V$)

$\sum (\gamma \lambda)^t \delta_t^V$ 
