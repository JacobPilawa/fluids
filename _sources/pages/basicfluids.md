# Basic Things about Fluids


## Fluid Approximation and the Fluid Element

### The Fluid Approximation

We will start with three criteria (hand-wavy, order of magnitude criteria). When these three criteria are met, only then can we apply the **fluid approximation.** Let's start by thinking about a fluid and fluid element (blue) of size $L$:

```{image} ../figures/fig1.png
:alt: fig1
:width: 600px
:align: center
```

1. $L$ has to be _large_ enough to contain many atoms or molecules. Mathematically, this is: $L \gg n^{-1/3}$, where $n$ is the mean number density of atoms. Note that $n^{-1/3}$ is roughly the mean atomic spacing. 
2. $L$ has to be _small_ enough that the "fluid properties" (temperature $T$, pressure $P$, mass density $\rho$, etc) we are looking at are constant within the fluid element. Mathematically, this is: $L \ll R$ where $R \sim \frac{Q}{|\vec{\nabla}Q|}$ where $Q$ can be any of our relevant quantities above. Note that $\vec{\nabla}$ is the gradient. 
3. The fluid is "collisional," meaning we have frequent interactions between particles, enough to "erase" the individual trajectories of particles in the fluid. These collisions can be anything – physical, Thomson scattering, anything – so long as they are frequent enough. Mathematically, we have: $L \gg \lambda$, where $\lambda$ is the mean free path of the fluid. **In this limit, frequent interactions allow particle distributions to depend only on macroscopic properties.**


### Counterexamples and an Example of a Fluid

**Counterexample**
A note about Criteria 3 – when does this note occur (i.e., when are they "collisionless?")? For example, in cosmology, cold dark matter (CDM) is a collisionless fluid (so are neutrinos), meaning extremely weakly interaction. Another example are photons, but that sort of depends on what is happening in the Universe. Photons rapidly interact with Thomson and Compton scattering depending on conditions. Photons _after_ recombination (or decoupling) are no longer a fluid. 

**Example** 
Let's look at an example for which we **can** find an $L$ to make us a fluid. Consider the Galactic HI disk:

* $n \sim 0.1 \text{ cm}^{-3} \rightarrow n^{-1/3} \sim 2 \text{ cm}$. 
* $R \sim 10 \text{ kpc} \rightarrow 3 \times 10^{22} \text{ cm}$. 
* $\lambda \sim \frac{1}{n\sigma} \frac{1}{(0.1 \text{ cm}^{-3})\times(10^{-15} \text{ cm}^{-2})} \sim 10^{16} \text{ cm}$

Putting these together, we don't have any problem finding an $L$ to obey Rules 1, 2, and 3! **No problem!**: $10^{16} \text{ cm}^{2} \ll L \ll 3\times 10^{22} \text{ cm}$. Note 
that if we have a weaker interaction like Thomson scattering $\sim 10^{-25} \text{ cm}^{2}$, we pretty soon cannot use fluid theory. 

---

## Derivatives: Eulerian versus Lagrangian

**A great thing to do on a Monday afternoon!**

Having this general concept in mind, let's move to a more mathematical and descriptive properties of these fluid elements moving throughout space. We must start with something we are familiar with – taking derivatives. 

We have two choices in tracking the fluid element. In the Lagrangian perspective, we move along _with_ the fluid element; the Eulerian approach looks at the time rate of change of a quantity while beign in a fixed frame. Note that numerically, there are many more considerations to Eulerian versus Lagrangian methods. 

---


### Deriving the Fluid Derivative 

```{image} ../figures/fig2.png
:alt: fig2
:width: 600px
:align: center
```



**Consier a fluid element** at $(\vec{r},t)$, then at $(\vec{r} + \delta \vec{r}, t + \delta t)$ at a later time. A time change of any quantity $Q$ (scalar, vector, tensor, ...) in a fluid element:

$$
\frac{DQ}{Dt} \equiv \lim_{\delta t \rightarrow 0} \frac{Q(\vec{r} + \delta \vec{r}, t+\delta t) - Q(\vec{r},t)}{\delta t}
$$


Let's Taylor expand:

$$
Q(\vec{r}+\delta \vec{r}, t + \delta t) - Q(\vec{r},t) 
$$

$$
= \underbrace{Q(\vec{r},t+\delta t) - Q(\vec{r},t)}_{\frac{\partial Q}{\partial t} \delta t} + \underbrace{Q(\vec{r} + \delta \vec{r}, t+\delta t) - Q(\vec{r},t+\delta t)}_{\delta \vec{r} \cdot \vec{\nabla}Q(\vec{r},t+\delta t)}
$$

$$
\text{second term} = \delta \vec{r} \cdot \left(\vec{\nabla} Q(\vec{r},t) + \delta t \cdot \frac{\partial}{\partial t} \vec{\nabla} Q(\vec{r},t)\right)
$$

Note that the $\delta \vec{r}$ and $\delta t$ terms are second order, and thus we can drop in the differentiation. 

Collecting our tmerms, we have:

$$
= \frac{\partial Q(\vec{r},t)}{\partial t} \delta t + \left(\delta \vec{r} \cdot \vec{\nabla}\right) Q(\vec{r},t)
$$

```{note}
One thing to be careful of in this class -- keep track of vectors and scalars! If we hav a vector equation, everything must be a vector. If we have a scalar equation, everything must be a scalar. 
```

Cleaning things up, we have:

$$
\boxed{\frac{DQ}{Dt} = \frac{\partial Q(\vec{r},t)}{\partial t} + \left(\vec{v}\cdot\vec{\nabla}\right)Q(\vec{r},t)}
$$

where 
* $\vec{v} = \frac{d\vec{r}}{dt}$ is the fluid velocity

The way to think about this equation is as follows:

$$
\text{rate of change \newline in the frame of the fluid} = \text{rate of change at fixed position } \vec{r} + \\ \text{ change due to fluid element moving to a new location}
$$
In other words, we have:

$$
\text{Lagrangian} = \text{Eulerian} + \text{ Advective/Convective Derivative Term}
$$

This motivates the use of the **Lagrangian operator**:

$$
\boxed{\frac{D}{Dt} = \frac{\partial}{\partial t} + \vec{v} \cdot \vec{\nabla}}
$$


### Example: Newton's 2nd Law Applied to a Fluid Element

$$
\vec{F} = m \frac{D \vec{v}}{Dt} = m \left(\frac{\partial \vec{v}}{\partial t} + \left(\vec{v} \cdot \vec{\nabla}\right)\vec{v}\right)
$$

Writing this as $F/m$ on the lhs gives the Navier-Stokes equation from last time!

**We emphasize here that the advection term is second order in $v$, making life extremely difficult.** 


Also, recall that, when we have $\vec{v}\cdot \vec{\nabla}$ . Be careful moving to different coordinate systems! Any time you are confused, go back to Cartesian (to comprehend). 

---

## Mass Conservation and the Continuity Equation


Consider a fluid of mass $M$, density $\rho$, velocity $\vec{v}$. Let's examine the time change of $M$. Note that $\rho \vec{v}$ is the flux. 

$$
\frac{\partial M}{\partial t} = \underbrace{- \int \rho \vec{v} \cdot \mathrm{d} \vec{S}}_\text{net flow through surface S}
$$

Let's re-write the left hand side in terms of density and the right-hand side using the divergence theorem:

$$
\frac{\partial}{\partial t} \int \rho \mathrm{d} V = - \int \vec{\nabla} \left(\rho \vec{v}\right) \mathrm{d}V
$$

The integrads should be equal, giving **the continuity equation in differential form (Eulerian framework)**:

$$
\boxed{\frac{\partial \rho}{\partial t} + \vec{\nabla} \left(\rho\vec{v}\right) = 0}
$$

If we use the Lagrangian operator we defined above, we have the **continuty equation in the Lagrangian framework**:

$$
\frac{D\rho}{Dt} + \rho \left(\vec{\nabla} \cdot \vec{v}\right) =0
$$

We will still likely use the Eulerian form mostly, but Lagrangian forms allow us to discuss _incompressible flow_. 

```{admonition} Incompressible flows/fluids

This means that the individual fluid elemnts preserve their density along their paths. When this is the case, we have:

$$
\frac{D\rho}{Dt} = 0 \rightarrow \vec{\nabla}\cdot \vec{v} = 0
$$

Incompressible flows are thus awesome because we can drop the divergence of $\vec{v}$ terms.

Another way of saying this: if the velocity field is divergence free, we have incompressible flows. 

To beat this to death: Incompressible flows are divergence free. Applications to come later. 

```

## Momentum Conservation: The Euler Equation, Pressure, and the Stress Tensor


There are two forces to consider: gravity and pressure. Let's consider them separately, starting with pressure.

### Pressure Forces

```{image} ../figures/fig3.png
:alt: fig3
:width: 600px
:align: center
```

**The force due to thermal pressure (gradient)** (not shear stress or other fancier forms, but just a classic pressure gradient giving a force) along a direction $\hat{n}$ (not necessarily normal to the surface) over surface $S$ due to pressure $P$ is:

$$
\vec{F} \cdot \hat{n} = - \int P \hat{n} \cdot \,\mathrm{d}\vec{S}
$$

Let's use the divergence theorem again, giving:

$$
\vec{F} \cdot \hat{n} = - \int \vec{\nabla} \left(P \hat{n}\right) \, \mathrm{d} V
$$

Note that $\hat{n}$ is not affected by the gradient, and thus:

$$
\vec{F} = - \int \vec{\nabla} P \, \mathrm{d} V
$$
We typically want the force per unit mass, which is:

$$
\frac{\vec{F}}{m} \approx - \vec{\nabla} P \cdot \frac{V}{m} = -\frac{1}{\rho} \vec{\nabla} P
$$

**An important note: if there is no gradient of pressure, there is no pressure force. Forces move things from high pressure to low pressure, and that is why we have the minus sign in front of the gradient.** 


### Gravitational Forces

Again, we want the force per unit mass due to gravity:

$$
\frac{\vec{F}}{m} = -\vec{\nabla} \Phi = \text{grav. potential} = -\frac{GM}{r^2} \hat{r}
$$

Let's take the surface integral of $\Phi$:

$$
\int \vec{\nabla} \Phi \cdot \, \mathrm{d}\vec{S} = \int \frac{GM}{r^2} \hat{r} \cdot \,\mathrm{d}\vec{S}
$$

Using the divergence theorem again (over a sphere for the right side), we have:

$$
\int \nabla^2 \Phi \, \mathrm{d}V = 4\pi G \int \rho \mathrm{d}V \text{ since} \int \frac{GM}{r^2} \mathrm{d}S = 4\pi GM
$$

This gives one of our favorite equations, **the Poisson equation**!:

$$
\boxed{\nabla^2 \Phi = 4\pi G \rho}
$$

### Collecting our Work

The force on a fluid element is thus:

$$
\vec{F} = m \frac{D\vec{v}}{Dt}
$$

**And substituting in our work, we have the Lagrangian form of the Euler equation for momentum conservation**

$$
\underbrace{\frac{D\vec{v}}{Dt}}_\text{fluid element accel.} = -\frac{1}{\rho} \underbrace{\vec{\nabla}P}_\text{press. grad.} - \underbrace{\vec{\nabla}\Phi}_\text{gravity}
$$


Re-writing for the Eulerian form, we have **the Euler Equation for momentum conservation:**

$$
\boxed{\frac{\partial \vec{v}}{\partial t} + (\vec{v} \cdot \vec{\nabla}) \vec{v} = -\frac{1}{\rho} \vec{\nabla}P - \vec{\nabla}\Phi}
$$



## A Real Quick Summary of our Three Fluid Equations

Above, we motivated and derived three fluid equations

```{admonition} The Continuity Equation

$$
\frac{\partial \rho}{\partial t} + \vec{\nabla} \left(\rho\vec{v}\right) = 0
$$

```

```{admonition} The Euler Equation

$$
\frac{\partial \vec{v}}{\partial t} + (\vec{v} \cdot \vec{\nabla}) \vec{v} = -\frac{1}{\rho} \vec{\nabla}P - \vec{\nabla}\Phi
$$

```

```{admonition} The Poisson Equation

$$
\nabla^2 \Phi = 4\pi G \rho
$$

```

Counting degress of freedom, we have $5$ real, independent equations. But how many unknowns? We have $\vec{v}$, $\rho$, $P$, and $\Phi$. 

We thus cannot uniquely solve our equations – we need one more to close our system of equations: **the equation of state** relating the ressure to the density. Once we have that, we have six equations with six unknowns.


## Energy Conservation and the Equation of State

## Simple Solutions: Hydrostatic Equilibrium, Polytropic Stars, and the Lane-Emden Equation

## Bernoulli's Principle