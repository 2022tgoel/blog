
Here's a cool problem you can solve with stochastic calculus:

Suppose you have an n-dimensional brownian motion $B_t$. What is the expected value of the time that it first exits the sphere of radius $a$?

Let $f(B_t)$ be the distance squared from the origin. Additionally, $\tau$ will be the first exit time. 

$E[f(B_\tau)] = a^2 = E\left[\int_0^\tau Af(B_t) dt \right]$ 

where

$Af(x) = \lim_{t \rightarrow 0} \frac{E^x[f(B_t)] - x}{t}$ 

this basically means that we can look at the expected instantaneous changes the the expected value of $f$.  The key observation is that this does not depend on $B_t$. 

$\frac{\partial^2 f}{\partial x_i \partial x_j} = 2$ and $\frac{\partial f}{\partial x_i} = 2x$

Through Ito's formula:

$Af(x) = df(B_t) = E[\sum_i 2B_i dB_i + \sum_{i, j} dB_i dB_j] = \sum_i dt = n dt$ 


$E\left[\int_0^\tau Af(B_t) dt \right] = E\left[\int_0^\tau ndt \right] = nE[\tau]$ 

Thus 

$E[\tau] = \frac{a^2}{n}$ 



### Ito Product Rule 

If $X$ and $Y$ are two Ito processes, then 

$d(XY) = XdY + YdX + d[X, Y]$ 

$[X, Y]$ is the joint quadratic variation $dXdY$. In a typical integral, this term can be ignored, but in a Intro process it can not be ignored. 

### Girsanov Theorem 

$\tilde{W} = W \int_0^t b(s) ds$

$Z(t) = \exp({-\int_0^t b(s) \cdot dW(s) - \frac{1}{2} \int_0^t |b(s)|^2 ds})$ 

$dZ(t) = -Z(t) b(t) \cdot dW(s)$ 

$\begin{align}d(\tilde{W}Z) &= Z(t) d\tilde{W_i} + \tilde{W_i} dZ - Z(t) \tilde{W}_i b(t) \cdot dW(s) \\ & =   Z(t) dW_i + Z(t) b_i(t)dt + (\tilde{W}_i + d\tilde{W}_i) dZ \\ & =   Z(t) dW_i + Z(t) b_i(t)dt + (\tilde{W}_i + dW_i + b_i dt) dZ \\ & = Z(t) dW_i + Z(t) b_i(t)dt -(\tilde{W}_i + dW_i) Z(t) b \cdot W \\ & = Z(t) dW_i + Z(t) b_i(t)dt -\tilde{W}_i Z(t) b \cdot dW - b_i Z(t) \\ & = Z(t) dW_i -\tilde{W}_i Z(t) b \cdot dW \end{align}$      

Since this only has $dW$ terms it is a martingale. 

https://www.math.cmu.edu/~gautam/sj/teaching/2016-17/944-scalc-finance1/pdfs/notes.pdf -- very concise and good introduction to these topics! 