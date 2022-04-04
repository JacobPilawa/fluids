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

---

We start here from last time. Recall the collisionless Boltzmann equation:


$$
\frac{Df}{Dt} = \frac{\partial f}{\partial t} + \dot{x}_i \frac{\partial f}{\partial x_i} + \dot{p}_i \frac{\partial f}{\partial p_i} = 0
$$

A standard way forward is to take velocity moments of the Boltmzann equation. There are infinite moments, by the way, constituting a "hierarchy." 

What do we mean by velocity moments? Let's examine.

0\. Zeroth Moment (no velocity weighting)

$$
\int d^{3} p \, v^0 f = \frac{N}{V} = \text{ number density of particles }
$$

1\. First Moment 

$$
\frac{\int d^3p \, \vec v\cdot f}{\int d^3p\, \cdot f} = \frac{1}{n} \int d^3p\, \vec v \cdot f = \langle \vec v\rangle
$$

2\. Second Moment

$$
\langle v_i v_j \rangle = \frac{1}{n} \int d^3p\, v_i v_j f 
$$

We typically use: $\sigma_{ij}^2 \equiv \langle v_i v_j \rangle - \langle v_i \rangle \langle v_j\rangle$. 

3\. $\ell$th moment:

$$
\langle v_i v_j \cdots v_\ell \rangle = \cdots 
$$

* But why does this help us? Each moment allows us to recover a macroscopic quantity! Taking moments takes us from individual particle pictures to macroscopic values.
* Above was moments in general, but let's apply this to the Boltzmann equation by taking its velocity moments. We then want to justify dropping higher order moments.

### Velocity Moments of the Boltzmann Equation

#### Take Zeroth Moment of BE

$$
\int d^3 p \, \left(\text{B.E}\right)
$$

This gives:

$$
\frac{\partial}{\partial t} \int d^3p \, f + \int d^3p \, \vec v \cdot \vec \nabla f - \underbrace{m \partial_i \Phi}_{\dot{p}_i} \cdot \int d^3p \, \frac{\partial f}{\partial p_i} = 0
$$

Note we can take gradients out of the integrals and we can also do integation by parts on the last term, assuming that $f \rightarrow 0$ at large $p$, and we find that the last term is $0$. Collecting terms:

$$
\boxed{\frac{\partial n}{\partial t} + \vec \nabla (n \cdot \langle \vec v \rangle ) = 0}
$$
And we recover the **continuity equation!** We interpret the velocity as the fluid velocity. 


#### Take First Moment of BE

$$
\int d^3 p \, v_j \left(\text{B.E.}\right)
$$

We have (with free index $v_j$)

$$
\frac{\partial}{\partial t} \int d^3 p \, v_j f + \int d^3p\, v_j v_i \partial_i f - m \partial_i \Phi \int d^3p \, v_j \frac{\partial f}{\partial p_i} = 0
$$

And we have three terms to deal with.

1\. Term 1: We have done this before. We get:

$$
\frac{\partial}{\partial t} \left(n\langle v_j\rangle\right) = n\frac{\partial \langle v_j \rangle}{\partial t} + \langle v_j \rangle \frac{\partial n}{\partial t}
$$

And we can use the continuity equation to get rid of the $\partial n / \partial t$. 

$$
= n \frac{\partial \langle v_j \rangle}{\partial t} - \langle v_j \rangle \partial_i (n\langle v_i\rangle)
$$
In a moment, we will see why we did this.


2\. Term 2:

We saw the second velocity moment before. The second term thus becomes:

$$
\partial_i \left(n\langle v_i v_j \rangle\right) = \partial_i \left(n \sigma_{ij}^2\right) + \partial_i \left(n\langle v_i\rangle \langle v_j\rangle\right)
$$

$$
 = \partial_i \left(n\sigma_{ij}^2\right) + \underbrace{\langle v_j\rangle \partial_i\left(n \langle v_i\rangle\right)} + n\langle v_i\rangle \partial_i \left(\langle v_j\rangle\right)
$$
**Hey! Look at that! From Term 1 above, we should recognize some familiar terms.**


3\. Term 3:

Here, we have:

$$
-\partial_i \Phi \cdot \int d^3p \, \cdot p_j \frac{\partial f}{\partial p_i} = - \partial_i \Phi \cdot \int d^3p\, \left(\underbrace{\frac{\partial}{\partial p_i}(p_j f)}_\text{surface term} - f\underbrace{\frac{\partial p_j}{\partial p_i}}_{\delta_{ij}}\right)
$$

And we assume the first term (the surface term) goes to $0$ since we thing $f$ falls off faster than $p$. Otherwise, this would be quite unphysical. So what are we actually left with?

$$
= \left(\partial_j \Phi\right) \cdot n
$$



4\. Adding our terms back together: 1+2+3 and simplifying a bit:

$$
\boxed{\frac{\partial }{\partial t}\langle v_j\rangle  + \langle v_i \rangle \partial_i \left(\langle v_j\rangle\right) = -\partial_j \Phi - \frac{1}{n}\partial_i \left(n\sigma_{ij}^2\right)}
$$

Let's compare this to our Euler equation!

$$
\frac{\partial \vec v}{\partial t} + \left(\vec v \cdot \vec \nabla\right)\vec v = -\vec \nabla \Phi - \frac{1}{\rho}\vec \nabla P
$$

We thus recover the Euler equation, **_almost_**. We need to map:

$$
\vec \nabla P \rightarrow \partial_i (\rho \sigma_{ij}^2)
$$
We actually encountered this before! We said earlier that the pressure is becoming the Stress tensor $\sigma_{ij}$. In the particle picture, this is just the velocity dispersion which is kinda like a pressure for particle pictures/in the kinetic picture. **Pressure is too simplistic.** We can actually write:

$$
\rho \sigma_{ij}^2 = P \delta_{ij} + \underbrace{\tau_{ij}}_\text{anisotropic stress tensor}
$$

What physical processes can contribute to non-zero $\tau_{ij}$:
* Viscosity
* Anisotropic stress in neutrinos 
    * They are weakly interacting and thus precisely not a fluid
* 


#### Take Second Moment of BE


$$
\partial d^3p\, v_i v_j \text{(B.E.)}
$$

This means to something like…

$$
\frac{\partial}{\partial t}\sigma_{ij}^2 + \cdots = \cdots \underbrace{\sigma_{ijk}}_\text{third vel. moment}
$$





* Note some patterns: 0th moment equation contains first moment and $n$
* First moment has second moment $\sigma$ and first moment
* Second moment will continue third moment and $\sigma$
* Thus we have an infinite hierarchy where higher order moments dictate lower moments...need to truncate or go to infinity!

* **Any time we take a moment of the BE equation, we will get one moment higher because of the momentum term in the BE! 
* 
* 

#### Take the $\ell$th velocity moment:

$$
\frac{\partial}{\partial t} \sigma_{ijk\cdots \ell} = 
$$

* The $\ell$th moment is coupled to the $(\ell -1)$ and $(\ell + 1)$ moments
* We assume a **closure relation** to truncate the infinite series – how you close the Boltzmann hierarchy is very important to avoid spuripous numerical problems.
* The photon and neutrino equations need high $\ell$. 
    * If you truncate hard (setting to 0, for example), it's a bit like you shake a rope with a very hard boundary condition (introducing back traveling waves). This spurious hard boundary comes back and affects the photon number density! So typically you use something like Bessel functions which are a bit smoother.
    * We typically go to $\ell$ of many thousands. 







































