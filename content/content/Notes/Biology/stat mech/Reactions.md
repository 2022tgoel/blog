


We have certain intuitive equilibrium conditions for a system + surrounding that isn't transferring heat or doing work
* $T_\text{system} = T_\text{surroundings}$. This makes sense if under the understanding that $T = \frac{\partial E}{\partial S}$ and that entropy always increases. Supposed $T_\text{system} > T_\text{surroundings}$ , then moving $\delta E$ energy from the system to the surroundings would result in $\delta S =- \frac{\delta E}{T_\text{system}} + \frac{\delta E}{T_\text{surroundings}} > 0$ change in the entropy. 
* $p_\text{system} = p_\text{surroundings}$. This is about an equilibrium of forces, if this weren't the case than the forces on either side wouldn't cancel out. 

### Enthalpy

$H = E  + PV$
$\Delta H = T dS + V dp + \mu dN = T dS + \mu dN$ under the constant pressure condition. 

$E = q + w$ 
$\delta H = \delta Q$


### Intuition

We have that

$dE = TdS - pdV + \mu dN$

We're going to add a powerful principle, which is that entropy always increases (2nd law of thermodynamics). 

This means that 

$d S_{surroundings} + d S_{system} \geq 0$

When a reaction occurs, there is both 

$dE_{surroundings} = TdS_{surroundings} - pdV_{surroundings} + \mu dN_{surroundings}$

and 

$dE_{system} = TdS_{system} - pdV_{system} + \mu dN_{system}$

Now, a key observation is that $dN_{surroundings} = 0$, because you're not actually changing the chemicals in the surroundings. 

Additionally, 

$p dV_{system} = -p dV_{surroundings}$ because that's how work works (assuming pressure is the same in the surroundings and the system). 

So, in the end, from conservation of energy, you get 

$TdS_{surroundings} = - TdS_{system} - \mu dN_{system}$ 

And if the temperatures are the same (a typical situation)

$dS_{surroundings} + dS_{system} = -\frac{\mu dN_{system}}{T} \geq 0$ 

Now, since we know this is gibbs free energy, this means

$\Delta G \leq 0$ for the reaction to be spontaneous. 

I was slightly bad with the notation here: $\mu dN_{system}$ should be thought of as $\sum_i \mu_i dN_i$ for each substance $i$ in the reaction.  

The assumptions we made here are:
* There is equal pressure inside the system and outside the system
* There is equal temperature inside and outside the system