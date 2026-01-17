
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

Thus, $E = TS - pV + \mu N$ 

Basically, the intuition you should be getting here is that there is no constant factor $C$ and that the derivatives have no dependence on $\lambda$ (that makes them intensive!)
## Important quantities

Hemholtz free energy: $F = E - TS$ 

Enthalpy: $H = E + pV$ 

Gibbs Free energy: $G = E + pV - TS = F + pV$

These must be **extensive properties**. 

## Entropy of Mixing

This is fundamental to why Gibbs free energy gives you a ratio. You can usually just think of entropy as the log of the number of position lists times the number of energy lists you can come up with which are consistent with the macroscopic variables. But because the particles are indistinguishable, you get **Gibb's paradox**, so you need to divide everything by $N!$. However, if you have two distinguishable types of particles, you can actually add some of these combinations back. In particular, you can add $\log{\frac{(N_A + N_B)!}{N_A! N_B!}}$ 

How does can you derive the concentration analyses that people use all the time from this? Good question. 

$\Delta \mathcal{G}_0$ is change in free energy under **standard conditions**. 

###### What is standard conditions? 
Standard conditions mean each species is at unit activity. Standard pressure: $p^\degree = 1$ . Standard concentration $c^\degree = 1$ M. Standard temperature: $T = 298.15 K$ is common.  Standard states are not the reacting system. They are an hypothetical world where you only have the one substance. 


Using stirling's approximation, we have that entropy of the mixing is $-\sum_i n_i \ln{n_i / n}$

For a reaction $A \rightarrow B$, we care about $[A]$ . Entropy of mixing is $\propto - [A] \ln{[A]} - (([B] + [A]).\text{stopgradient}() - [A]) \ln{([B] + [A]).\text{stopgradient}() - [A])}$  (Alas my notation is so cursed...)
 
Then means that $\frac{\partial G}{\partial [A]} = - \ln{[A]} + \ln{[B]} = \ln{\frac{[B]}{[A]}}$ . Now we are getting something that looks like the concentration of products to reactants. 




