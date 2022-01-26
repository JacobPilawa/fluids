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

### Counting Degress of Freedom

Above, we motivated and derived three fluid equations:

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


As we saw above, we need one more piece of information to close fluid equations. We will start with a closer look at pressure.

### A Closer Look at "Pressure"

Here are some examples:

* Thermal pressure
    * The most familiar pressure to us – the $P$ in $PV=nRT$!
    * Due to **isotropic** random velocities of molecules in a gas
* Ram pressure
    * Something ramming into something else – important for thinking about galaxy collisions/galaxies moving through clusters, hot gas, and dark matter haloes
    * Due to the **bulk** motion 
* Radiation pressure
    * Due to photons imparting momenta from themselves to other objects

What are the units of pressure?

$$
[P] = \frac{\text{force}}{\text{area}} = \text{momentum flux}
$$

What do we mean by momentum flux? Let's examine units:

$$
\text{force/area} \propto \frac{m\cdot v}{t \cdot L^2} \propto \frac{p}{t\cdot\text{area}} = \text{ momentum flux}
$$

### Generalizing Pressure to the Stress Tensor

With this in mind, we can move on by generalizing pressure to a more fundamental object – the **stress tensor** $T_{ij}$. This is a rank $2$ tensor, which we can think of as $3\times3$ matrix. 

```{note}
In general, forces across a surface do not have to be **perpendicular** to the surface. The natural way to express these more general forces are with the stress tensor. 

The force in some direction $i$ is given by:

$$
F_i = T_{ij} S_{j}
$$

where $S_j$ is the surface and $T_{ij}$ is the force per area in direction $i$ action on a surface with normal in the $j$ direction. Note that repeated indices are implictly summed over: if we want to know $F$ in the direction of $x$, we have $F_{i} = T_{xx}S_{x} + T_{xy}S_{y} + S_{xz}S_{z}$. 

```

#### An Example:

A surface in the $x-y$ plane, whose normal is in $\hat{z}$. 

```{image} ../figures/fig4.png
:alt: fig4
:width: 600px
:align: center
```

In this setup:

* $T_{zz}$ is the normal stress. 
* $T_{xz}$ and $T_{yz}$ have similar interpretations – forces in the plane are shear forces/shear stresses. 
* Just to stress again: **the first index is the direction of the force.** 

### Revisiting the Fluid Equations with the Stress Tensor

Recall the Continuity Equation:

$$
\frac{\partial \rho}{\partial t} + \partial_j \left(\rho v_j\right) = 0 \text{       } (1)
$$

where 

$$
\partial_j \equiv \frac{\partial}{\partial x_j}
$$

And the Euler Equation:

$$
\frac{\partial v_i}{\partial t} + v_j \partial_j v_i  = -\frac{1}{\rho} \partial_i P - \partial_i \Phi \text{        } (2)
$$

We will now re-write (2) in a more interesting form with some algebra. 

Before we continue, note that mass flux is the same thing as momentum density:

$$
\rho v_i \sim \text{momentum}/\text{volume} \sim \text{momentum density}
$$


Also:

$$
\frac{\partial}{\partial t} \left(\rho v_i\right) = \rho \frac{\partial v_i}{\partial t} + v_i \frac{\partial \rho}{\partial t}
$$

We will use $(2)$ to replace $\frac{\partial v_i}{\partial t}$ in the first term.:

$$
= -\rho v_j \partial v_i - \partial_i P - \rho \partial_i \Phi
$$
And we will use $(1)$ to replce the second term:

$$
\frac{\partial \rho}{\partial t} = - v_i \partial_j \left(\rho v_j\right)
$$

Thus:

$$
\frac{\partial}{\partial t} \left(\rho v_i\right) = -(\rho v_j) \partial_j v_i - \partial_i P - \rho \partial_i \Phi - v_i \partial_j \left(\rho v_j\right)
$$

$$
= -\partial_j \left(\rho v_i v_j + P \delta_{ij}\right) - \rho \partial_i \Phi
$$

This motivates:

$$
\boxed{T_{ij} \equiv \rho v_i v_j + P\delta_{ij}}
$$

With thjis definition, our fluid equation becomes:

$$
\boxed{\frac{\partial}{\partial t} \left(\rho v_i\right) = -\partial_j T_{ij} - \rho \partial_i \Phi}
$$

This above equation is sometimes called the **Conservative Form of teh Moemntum equation/Euler Equation.** It is basically the Euler Euqation in a different form. It looks very analogous to the contunity equation! Note that his is the $1st$ velocity moment of the phase-space distribuiton. We can then take the second and third moments to build Jeans equations. 

A complete derivation of the above is here:

```{image} ../figures/fig5.png
:alt: fig5
:width: 600px
:align: center
```

Let's look at the equation for $T_{ij}$ a bit more closely:


$$
T_{ij} \equiv \underbrace{\rho v_i v_j}_\text{ram pressure} + \underbrace{P\delta_{ij}}_\text{thermal pressure}
$$

Note that we didn't do anything special to get the ram pressure term. It really came from being embedded in the Euler equation. 

#### Example: Fluid Flow Along A Pipe


Let's consider fluid flowing along a part in the $\hat{x}$ direction: $\vec{v} = v \hat{x}$. 


```{image} ../figures/fig6.png
:alt: fig6
:width: 600px
:align: center
```

* $T_{zz}$ and $T_{yy}$ are just pressure! We have no velocity along $y$ or $z$. 
* We also have no off diagonal terms since $v_{y}$ and $v_z$ are both $0.$
* $T_{yy}$ and $T_{zz}$ have pressure.
* $T_{xx}$ has both pressure and ram pressure. $T_{xx} = P + \rho v^2$. 



Some comments for the record:

* $T_{ij}$ can have other terms than shown here. For example, due to viscosity, magnetic pressure, neutrino (important for CMB anistropy) or other anisotrpic stresses. Note that the example above have $0$ off-diagnoal terms since we have isotropic stress. 
* **Ram pressure** is relevant for gas content in galaxies that reside in galaxy clusters. Think about the term "ram stripping" which is often needed to explain the red colors of galaxies in cluster. 





## Energy Conservation and the Equation of State



### A Quick Thermodynamics Review

Our favorite class from undergrad...but not as great as E&M. 

```{admonition} The First Law

$$
\mathrm{d}\,Q = T\,\mathrm{d}s = \mathrm{d}\,\mathcal{E} =+ P\,\mathrm{d}V
$$

```

We also had the idea of **specific heat** $C_V \equiv \left(\frac{\partial Q}{\partial T}\right)_V = \left(\frac{\partial \mathcal{E}}{\partial T}\right)_V$ when we hold volume fixed. This allows us to re-write the First Law as:

$$
\mathrm{d}Q = C_V \,\mathrm{d}T + P \,\mathrm{d}V
$$

We also had $C_P$ where we hold the pressure consant, and we can relate $C_V$ to $C_P$. 

#### An Ideal Gas

Only obeyed for:

1. Randomly moving atoms or molecules. 
2. Intermolecular/atomic forces are negligible. 
3. Negligible volume occupied by the molecules (point-like particles). 

In this ideal gas limit, **pressure is entirely due to kinetic motion of the particles.** For this kind of gas, we have the following **Ideal Gas Law Equation of State**:

$$
\boxed{PV = N k_b T \rightarrow P = nk_b T}
$$

We can now take derivatives!

$$
P \, \mathrm{d}V + V \, \mathrm{d}P = Nk_b \, \mathrm{d}T \text{ assuming} \,\mathrm{d}N=0
$$
Go back to the First Law:

$$
\mathrm{d}Q = C_V \mathrm{d}T + P \mathrm{d}V
$$

$$
\mathrm{d}Q = C_V + Nk_b \mathrm{d}T - V\mathrm{d}P
$$

We can now write:

$$
\boxed{\left(\frac{\partial Q}{\partial T}\right)_P \equiv C_P = C_V + Nk_b}
$$

#### Adibatic, Ideal Gas Equation of State

In the special gas of an adiabatic (no heating or cooling due to dissipitative processes, $\mathrm{d}Q =0$) ideal gas, a bunch of other nice things happen!

We first have a new expression of the First Law of Thermodynamics:

$$
C_V \mathrm{d}T + P\mathrm{d}V = 0
$$

We can use $PV=Nk_bT$:

$$
C_V \mathrm{d}T + \frac{NkT}{V}\mathrm{d}V = 0 \rightarrow \frac{\mathrm{d}T}{T} = -\frac{Nk}{C_V} \frac{\mathrm{d}V}{V}
$$

The solution gives:

$$
\boxed{T \propto V^{-\frac{Nk_b}{C_V}}}
$$
Remember our goal: we wanted to relate **pressure** to **density**, and we now have temperature and volume. How do we make the last step? Well we have $P \propto T/V \propto V^{-\frac{Nk}{C_V}-1}$. This exponent is nothing but $C_P/C_V$!:

$$
\boxed{P \propto V^{-\frac{C_P}{C_V}} } \text{ or } \boxed{P \propto V^{-\gamma}}
$$


where $\gamma \equiv C_P/C_V$ is the **adiabatic index.** Since $\rho \propto V^{-1}$, we have **the Equation of State for an Adiabticc, Ideal Gas**:

$$
\boxed{P = k \rho^{\gamma}}
$$

This is an exmaple of a baro-tropic equation of state – the pressure is entirely detemrined by $\rho$. 


#### Adiabatic Index

Recall that $\gamma\equiv \frac{C_P}{C_V}$. 

For a **monatomic gas**, $\mathcal{E} = \frac32 NkT \rightarrow C_V = \frac32 Nk \rightarrow C_P = \frac52 Nk$.  

This gives 

$$
\boxed{\gamma_{monatomic}  = \frac{5}{3}}
$$

For a diatomic gas: $\mathcal{E} = \frac52 NkT \rightarrow C_V = \frac52 Nk \rightarrow C_P = \frac72 Nk$, and thus:

$$
\boxed{\gamma_{diatomic} = \frac75}
$$



## Simple Solutions: Hydrostatic Equilibrium, Polytropic Stars, and the Lane-Emden Equation

## Bernoulli's Principle