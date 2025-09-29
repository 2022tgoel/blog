Let's apply the analysis from the intro to ideal gases.

Recall

* **Maxwell-Boltzmann**: traditional scenario where the particles are distinguishable
* **Bose-Einstein**: The particles are indistinguishable, and can occupy any number of energy levels
* **Fermi-Dirac**: The particles are indistinguishable, and each can only occupy one energy level. 


## Microcanonical Ensemble

Since they are all kind of similar, let's just apply method of most probable values to the BE case

$W\{n_i\} = {g_i + n_i - 1 \choose g_i - 1}$  

Where $g_i$ is the number of energy levels for the $i$th group. 

$\ln{W\{n_i\}} \approx (g_i + n_i)\ln{(g_i + n_i)} - n_i \ln{n_i} - g_i \ln{g_i}$ 

$\mathcal{L} =\sum( (g_i + n_i)\ln{(g_i + n_i)} - n_i \ln{n_i} - g_i \ln{g_i}) - \lambda \sum n_i - \gamma \sum \epsilon_i n_i$ 

$\frac{\partial \mathcal{L}}{\partial n_i} = \ln{\frac{g_i + n_i}{n_i}} - \lambda - \gamma \epsilon_i = 0$

solving this gives 

$n_i^* = \frac{g_i}{e^{\alpha + \beta \epsilon_i} - 1}$ 

## Canonical Ensemble








