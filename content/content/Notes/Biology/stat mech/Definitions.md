
We have that 


$dU = T dS  - p dV + \mu dN$ 


Which gives us $U(S, V, N)$ assuming constant $T, p, \mu$ 


An **extensive property** is one whose magnitude is additive for subsystems. If you have a subsystem with volume $V_1$ and a subsystem with volume $V_2$, then the volume of the total system is $V_1 + V_2$. Thus, volume is an extensive property. 

However, if you look at pressure, it's clearly not additive like this. 

An **intensive** property is one that is not changed when you divide a system into subsystems. If you took a system with pressure $p$ and split it in half, you would get two subsystems of pressure $p$. 

extensive properties:
* $V$
* $N$
* $S$. The short proof is that if sys 1 has $\Omega_1$ states and sys 2 has $\Omega_2$ states, then the combined sys has $\Omega_1 \Omega_2$ states, so $S = S_1 + S_2$ (additive under log). 


intensive properties:
* $p$
* $T$. If you go back to thinking about temperature as the average kinetic energy per particle, this becomes obvious, though you have to relate it to $\frac{\partial E}{\partial S}$  
* $\mu$ 


From this, it is clear that $\lambda U = U(\lambda S, \lambda V, \lambda N)$

#### Euler's theorem for homogenous functions

Suppose you have a homogenous function $\lambda f(x_1, x_2, ... x_n) = f(\lambda x_1, \lambda x_2, ... \lambda x_n)$. Define $g(\lambda) = f(\lambda x_1, \lambda x_2, ... \lambda x_n)$. 

Then 

$g'(\lambda) = f(x_1, x_2, .., x_n) = \sum_i x_i \frac{\partial f}{\partial x_i}$. 


## Important quantities

Hemholtz free energy: $F = E - TS$ 

Enthalpy: $H = E + pV$ 

Gibbs Free energy: $G = E + pV - TS = F + pV$

These must be **extensive properties**. Proof