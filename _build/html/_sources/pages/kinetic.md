# Kinetic Theory

This can be an entire class, and we are about to open a huge can of worms. Plasma physics is an example. CMB anisotropies are also an example. 

Recall the fluid approximation from our first lectures. The fluid treatment is only valid when a fluid element of size $R$ can be found where:

1\. $R \gg n^{-1/3}$ 

2\. $R \gg \ell_{mfp}$ 

3\. $R \ll \frac{Q}{|\vec \nabla Q|}$ 

When one of these break down, we cannot use fluid analysis. We instead have to consider kinetic theory.

## Phase Space Distribution Functions and the Boltzmann Equation



**Phase space is a six dimensional parameter space of positions $\vec x$ and conjugate momenta $\vec p$.** The phase space distribution function $\mathcal{f}$ can be thought of as a probability distribution $\mathcal{f}(\vec x, \vec p, t)$. The Boltzmann equation governs the evolution of $\mathcal{f}$. We will find that the lowest moments of the Boltzmann equation map directly into the fluid equations that the fluid equations do not deal with. 

We also have to consider the "phase space volume" centered at a $(\vec x, \vec p) \rightarrow (\vec x + \Delta \vec x, \vec p + \Delta \vec p) = d^3\vec xd^3 \vec p$. Note that the phase space volume has units of $h^3$, the Planck constant.

The number of particles in phase space volume $d^3 \vec x d^3 \vec p$ around point $\vec x, \vec p$ is:

$$
n = \int \mathcal{f}(\vec x, \vec p, t) \, \mathrm{d}^3\vec x \, \mathrm{d}^3\vec p  
$$
We can now write down the phase-space continuity equation:

$$
\frac{\partial \mathcal{f}}{\partial t} + \frac{\partial}{\partial x_i} \left(\underbrace{\dot{x}_i \mathcal{f}}_\text{flux out of spatial volume}\right) + \frac{\partial}{\partial p_i} \left(\underbrace{\dot{p}_i \mathcal{f}}_\text{flux out of momentum volume}\right) = 0
$$

This is analgous to our continuity equation in the fluid case:

$$
\frac{\partial \rho}{\partial t} + \vec \nabla (\rho \vec v) = 0
$$
We can re-write our equation as:

$$
\frac{\partial f}{\partial t} + \dot{x}_i \frac{\partial f}{\partial x_i} + \dot{p}_i \frac{\partial f}{\partial p_i} + f\left(\underbrace{\frac{\partial \dot{x}_i}{\partial x_i} + \frac{\partial \dot{p}_i}{\partial p_i}}_\text{0 from Hamilton eq.}\right) = 0
$$

Recall the Hamiltonian is $H$ and the Hamilton equation is:

$$
\dot{x}_i = \frac{\partial H}{\partial p_i}
$$

$$
\dot{p}_i = -\frac{\partial H}{\partial x_i}
$$

These two equations tell us that:

$$
\frac{\partial \dot{x}_i}{\partial x_i} + \frac{\partial \dot{p}_i}{\partial p_i} = 0 
$$
$$
\frac{}{}
$$
And now we have the **Boltzmann equation**:

$$
\frac{\partial f}{\partial t} + \dot{x}_i \frac{\partial f}{\partial x_i} + \dot{p}_i \frac{\partial f}{\partial p_i} = 0
$$

Or more elegantly:

$$
\boxed{\frac{Df}{Dt} = 0}
$$

This is the **collisionless Boltzmann equation.** Sometimes we have processes which change the number density. If we had collisonal terms, this would look something like:

$$
\frac{Df}{Dt} = \underbrace{\left(\frac{\partial f}{\partial t}\right)_C}_\text{collisional term}
$$








