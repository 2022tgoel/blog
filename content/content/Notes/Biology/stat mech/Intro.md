
This is a summary of some of the interesting parts of http://linux0.unsl.edu.ar/~froma/MecanicaEstadistica/Bibliografia/PathriaBeale.pdf, with the goal of understanding Gibbs free energy from a very foundational standpoint so that I can understand chemical reactions theory. 


Statistical mechanics has the notion of entropy for a probability distribution $p_i$. This is defined as $\sum_i p_i \log { p_i }$. In stat mech, this often simplified to $k\log\Omega$, where $\Omega$ is a representation of the number of states a system could be in. This definition is equivalent if every state is equally likely, which is an intuitive but not obvious claim.  

$Ω(E)=\frac{1}{h^{3N}N!}​∫δ(E−H(p, q))d^{3N}pd^{3N}q,$

## Liouville's theorem

Suppose you have some prior probability (density) function $\rho$ in the space of possible states, and you want to understand how it evolves over time. Mathematically, you want to understand $\frac{d}{dt} \int_\omega \rho d\omega$ for a volume element $\omega$, which is $-\int_\sigma \rho \vec{v} \cdot \hat{n} d \sigma$, or, through the divergence theorem, $-\int_\omega \nabla \cdot (\rho \vec{v}) d\omega$.

This can be expanded as 

$-\int_\omega \sum_{i = 0}^{3N} (\frac{d\rho}{d q_i} \dot{q_i}  + \rho \frac{d\dot{q_i}}{dq_i} ) + \sum_{i = 0}^{3N} (\frac{d\rho}{d p_i} \dot{p_i} + \rho \frac{d\dot{p_i}}{dp_i}) d\omega$

So the ultimate equation is

$\frac{d \rho}{dt} = -\int_\omega \sum_{i = 0}^{3N} (\frac{d\rho}{d q_i} \dot{q_i}  + \rho \frac{d\dot{q_i}}{dq_i} ) + \sum_{i = 0}^{3N} (\frac{d\rho}{d p_i} \dot{p_i} + \rho \frac{d\dot{p_i}}{dp_i}) d\omega$ 

Up till now, we are just using some properties of the integral that we are interested in evaluating. Now we will use some physics.


$H = K + U = \frac{1}{2m} \sum p_i^2 + U(q)$ 

$\frac{dH}{dt} = \sum \frac{p_i}{m} \dot{p_i} + \sum \frac{dU}{dq_i} \dot{q_i}$ 

We'll make use of Hamilton's equations here:  $\dot{q_i} = \frac{p_i}{m} = \frac{\partial H}{\partial p_i}$ and $\dot{p_i}  = - \frac{dU}{dq_i} = -\frac{\partial H}{\partial q_i}$ , this shows that some terms will cancel. 

This allows us to simplify to 

$\frac{d \rho}{dt} = -\int_\omega \sum_{i = 0}^{3N} \frac{d\rho}{d q_i} \dot{q_i} + \sum_{i = 0}^{3N} \frac{d\rho}{d p_i} \dot{p_i} d\omega$ 

If you think of $\rho$ along a trajectory $\rho(t, p(t), q(t))$, this means that $\frac{d\rho(t, p(t), q(t))}{dt} = 0$. 

This leads to a deep result: in the geometry of phase space,  $\rho$ is constant along a trajectory. It's not like the trajectories "cluster up" in a certain part of the phase space and than "spread out" (which could be a consequence of different laws of physics). Every point in phase space is equally likely. 

#### The Caveat
Now it actually turns on phase space is not the right space for microstates, because particles are *indistinguishable* so microstates that are separate points in phase space might not actually be the same state. So, for example, a momentum coordinate of $(2, 1, 2)$ for 3 particles is the same as $(2, 2, 1)$ and $(1, 2, 2)$, so it can have a weight of 3, while the state $(1, 2, 3)$ will have a weight of 6. So in the world of indistinguishable particles, every distinct microstate isn't actually equally likely. Now why this doesn't change the definition of entropy isn't super clear to me, maybe there is some simplification going on. 

## Microcanonical and Canonical Ensembles

Having established that, we're going to switch from expressing states as points in phase space to expressing them as lists of occupation numbers $\{n_r\}$. This is basically expressing $2^N$ momentum coordinates, and ignores the position degrees of freedom, which can be thought of as a scalar independent from E.

The number of states at energy levels $[E,E+ dE)$ is $\propto V 4 \pi p^2 dp$ which knowing that $E = \frac{p^2}{2m}$ and $dE = \frac{p}{m} dp$ is $\propto V 4 \pi \sqrt{2mE } m dE$.   

$\Omega(V, \mathcal{E}, N) \propto \sum_{\{n_r\}}' W\{n_r\}$  where the $\{n_r\}$ must satisfy $\sum_r n_r = N$ and $\sum_r e_r n_r = \mathcal{E}$.   

$W\{n_r\} = \frac{N!}{n_0!n_1!n_2!...}$ as can be seen from the caveat in the previous section. 

These are some of the fundamental math techniques for analyzing the canonical ensemble: 
#### Method of most probable values

Say we want to find the argmax of $W\{n_r\}$. Well in the large N regime we can apply Stirling's formula ($\ln{n!} = n\ln{n} - n$) to get that 

$W\{n_r\} = \frac{N!}{n_0!n_1!n_2!...} \approx N\ln{N} - \sum n_r \ln{n_r}$ , we can use Lagrange multipliers to maximize this 

$L(\{n_r\}) = N\ln{N} - \sum n_r \ln{n_r} - \alpha \sum n_r - \beta \sum e_r n_r$ 

$\frac{dL}{dn_r} = -\ln{n_r} - 1 - \alpha - \beta e_r$

$n_r \propto e^{\alpha + \beta e_r}$ 

#### Method of mean values

Suppose we want to find 

$\langle n_r \rangle = \frac{\sum_{\{n_r\}} n_r W{\{n_r\}}}{\sum W{\{n_r\}}}$  

If we let 

$\tilde{W}\{n_r\} = \frac{N!\omega_0^{n_0} \omega_1^{n_1}...}{n_0!n_1!...}$ 

Then 

$\langle n_r\rangle = \omega_r \frac{\partial}{ \partial \omega_r} (\ln\sum \tilde{W}\{n_r\} )$ 

$\sum \tilde{W}\{n_r\}$ is almost $(\sum \omega_r)^N$ but the is the additional constraint that $\sum e_r n_r = \mathcal{E}$. Fortunately, we can also encode this as a constraint in the generating function.

The new generating function is $(\sum \omega_r z^{e_r})^N$ where we want the coefficient on the term that is $z^\mathcal{E}$. We can extract this through 

$\frac{1}{2 \pi i} \int z^{-\mathcal{E} - 1} (\sum \omega_r z^{e_r})^N dz$ (Cauchy's integral formula)

Some math proof of it: 

$\int z(\theta)^i dz = \int_0^{2\pi} (\cos(\theta) + i\sin(\theta))^n (-\sin(\theta) + i \cos(\theta))d\theta = \int_0^{2\pi} (\cos((n + 1) \theta + \frac{\pi}{2}) + i\sin((n + 1) \theta  + \frac{\pi}{2})) d\theta$ 
which is $2 \pi i$ when $n = -1$ and $0$ otherwise. 