
SGD on an underconstrained linear system where $n < d$. 

$f_w(x) = x^T w$ 

$X w = y$ 

There an an infinite number of solutions. 

Suppose we think that the "best" solution is that where the the loss landscape is smoothest. The hessian for $w$ is $X^T \beta(y) X$, where $\beta$ is the Hessian for loss wrt $y$. 

the gradient is 

$\nabla_w = X^T \frac{\partial L}{\partial y}$    

which notably means that updates to $w$ are a linear combination of the data. 

$\min_{w | Xw = y} ||w||_2^2$ 

lagrange multipliers

$w = \alpha_1 x_1 + \alpha_1 x_2 + \alpha_1 x_3 ...$ 

Where $\alpha_i$ are the lagrange multiplier coefficients. Thus $x$ is a solution of the form $X X^T \alpha$ 


