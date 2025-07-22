https://tcpc.me/2024/08/12/decaying-lights.html

$E[y] = \sum_t[(1 - (1-p)^t)^n - (1 - (1-p)^{t-1})^{n}]t$

consider $p = 0.5$ and $T = 1$

$E[y] = \sum_{t > 1} [(1 - 0.5^t) - (1 - 0.5^{t-1})]t$

$E[y] = \sum 0.5^t t$ 

Let $r = (1-p)$

$E[y] = \sum_t \left[\sum_{0 \leq i \leq n} {n \choose i} (-1)^i (r^t)^i t - \sum_{0 \leq i \leq n} {n \choose i} (-1)^i (r^{t-1})^i \right]t$  

$= \sum_t \left[\sum_{1 \leq i \leq n} {n \choose i} (-1)^i (r^i)^t t - \sum_{1 \leq i \leq n} {n \choose i} (-1)^i (r^i)^{t-1} \right]t$ 

$= \sum_{1 \leq i \leq n} {n \choose i} (-1)^i \sum_t [(r^i)^t - (r^i)^{t-1}] t$

$= \sum_{1 \leq i \leq n} {n \choose i} (-1)^i \frac{r^i - 1}{(1-r^i)^2}$

$= \sum_{1 \leq i \leq n} {n \choose i} (-1)^i  \frac{-1}{1-r^i}$

$= \sum_{1 \leq i \leq n} {n \choose i} (-1)^{i+1}  \sum_k (r^i)^k$

$=   \sum_k \sum_{1 \leq i \leq n} {n \choose i} (-1)^{i+1}(r^k)^i$ 

$\sum_k (1 - (1 - r^k)^n )$

Does this work work $n=2$?

$= 4 - \frac{4}{3} = 2.667$

yeah seems legit.



$E[z] = \sum_t x^t t$

$E[z] - xE[z] = \sum_{t > 1} x^t = \frac{x}{1-x}$

$E[z] = \frac{x}{(1-x)^2}$ 

$E[x] = p + (1-p)(1 + E[x])$

$pE[x] = 1$

$E[x] = \frac{1}{p}$ 

$E[x] = \sum p(1-p)^{n-1} n$ 

$E[x] - (1-p) E[x] = \sum p (1-p)^{n-1} = 1$ 



$E[y] - (1 - (1-p)^n) E[y] = \sum_n (1 - (1-p)^n)^n$ 

