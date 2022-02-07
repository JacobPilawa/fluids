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


```{image} ../figures/fig6.png
:alt: fig6
:width: 600px
:align: center
```



Let's consider fluid flowing along a part in the $\hat{x}$ direction: $\vec{v} = v \hat{x}$. 


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


#### An Aside: Energy in an Ideal Gas

Let's review equations from last time, and then derive the enery conservation equation.

Last time, we saw:

* The First Law: $\mathrm{d}Q = \mathrm{d}\mathcal{E} + P\mathrm{d}V$
* Adiabatic, Ideal Gas Law: $P = k \rho^\gamma$, where $\gamma \equiv \frac{C_p}{C_v}$ is the adiabatic index. 
    * This is a very good example of an **equation of state**.  We will see more!
    * A few words about $k$:
        * This coefficient $k$ can be shown to be related to **entropy** $S$: 

$$
\boxed{k = e^{\frac{S(\gamma-1)}{k_b}}}
$$

We will push this a bit farther –

Assuming adiabatic expansion, we have:

$$
dQ = 0 \rightarrow \mathrm{d}\mathcal{E_{permass}} = -P \frac{\mathrm{d}V}{m} = -P  \mathrm{d}\left(\frac{1}{\rho}\right)
$$

Using our equation of state $P\propto \rho^\gamma$  we have:

$$
\mathrm{d}\mathcal{E}_{permass} = \frac{k \rho^{\gamma}}{\rho^2} \mathrm{d}\rho \rightarrow \mathcal{E}_{permass} = \frac{k}{\gamma-1}\rho^{\gamma-1}
$$

We can re-write this last expression for the internal energy:

$$
\mathcal{E}_{permass} = \frac{1}{\gamma-1}\frac{P}{\rho}
$$

**Thus, we have shown that the internal energy (per unit mass) is:**

$$
\boxed{\mathcal{E}_{permass} = \frac{1}{\gamma-1} \frac{P}{\rho} \rightarrow P = \rho(\gamma-1)\mathcal{E}_{permass}}
$$

Or, we can do this in terms of volume instead of mass:

$$
\boxed{\mathcal{E}_{pervolume} = \frac{1}{\gamma-1} P}
$$



### Energy Density in an Ideal Gas:

$$
\underbrace{E}_\text{energy density} = \rho \left(\underbrace{\frac12 v^2}_\text{kinetic} + \underbrace{\Phi}_\text{potential} + \underbrace{\mathcal{E}}_\text{int. energy per mass}\right)
$$

We want to see how the total energy changes with time:

The first two terms are easy to deal with, so let's begin with the **internal energy change as a function of time**. 

$$
\frac{D \mathcal{E}}{Dt} = 
$$

Let's start with: $\rho=M/V$, and  $\mathrm{d}\mathcal{E} = \mathrm{d}Q - P \mathrm{d}V$. This expression tells us that:

$$
\frac{DV}{Dt} = -\frac{M}{\rho^2}\frac{D\rho}{Dt}
$$

This makes our expression for the internal enegy:


$$
\frac{D \mathcal{E}}{Dt} =  \frac{P}{\rho^2}\frac{D\rho}{Dt} - \dot{Q}_{cool}
$$

where $\dot{Q}_{cool}$ is the cooling function (per mass). Note that it is convention to say that it is a _cooling_ function (because of the minus sign). $\dot{Q} > 0$ is fluid is cooling. $\dot{Q} < 0$ for heating. This depends on the microphysics. 

We now want to calculate the full change in energy density:

$$
\frac{DE}{dt} = \frac{E}{\rho}\frac{D\rho}{Dt} + \rho\left(\vec{v} \cdot \frac{D \vec{v}}{Dt} + \frac{D\Phi}{Dt} + \frac{P}{\rho^2}\frac{D\rho}{Dt} - \dot{Q}_{cool}\right)
$$

This looks complicated, but we know lots of stuff!

The first term is related to the continuity equation.

$$
\frac{E}{\rho}\frac{D\rho}{Dt} = -E \vec{\nabla}\cdot \vec{v}
$$

The second term of $\vec{v} \cdot \frac{D\vec{v}}{Dt} = -\vec{v} \cdot \vec{\nabla} P - \rho \vec{v} \cdot \vec{\nabla}\Phi$ from the Euler equation. 

The potential derivative term can be written as:

$$
\frac{D\Phi}{Dt} = \rho \frac{\partial \Phi}{\partial t} + \rho \vec{v} \cdot \vec{\nabla}\Phi
$$

And the last term, from Contunity equation:

$$
\frac{P}{\rho^2} \frac{D\rho}{Dt} = -P \vec{\nabla}\cdot \vec{v}
$$

If you stare at these equations, some nice cancellation happens! Collecting terms, we have:

$$
\frac{DE}{Dt} = -\left({E+P}\right) \vec{\nabla} \cdot \vec{v} - \left(\vec{v} \cdot \vec{\nabla}\right)P + \rho\frac{\partial \Phi}{\partial t} - \rho\dot{Q}_{cool}
$$

The left hand side, by the way, is:

$$
\frac{DE}{Dt} = \frac{\partial E}{\partial t} + \left(\vec{v} \cdot \vec{\nabla}\right)E
$$

Notice! The right hand side and left hand side have some common terms, now! **Magic happens when we put this into a suggestive form!**

$$
\boxed{\frac{\partial E}{\partial t} + \vec{\nabla} \cdot \left(\left[E+P\right]\vec{v}\right) = -\rho \dot{Q}_{cool} + \rho \frac{\partial \Phi}{\partial t}}
$$

This is **energy conservation equation!** This is worth a note of its own, noting that $E$ is the energy density:

```{admonition} Energy Conservation Equation


$$
\boxed{\frac{\partial E}{\partial t} + \vec{\nabla} \cdot \left(\left[E+P\right]\vec{v}\right) = -\rho \dot{Q}_{cool} + \rho \frac{\partial \Phi}{\partial t}}
$$


where $E$ is the energy density.

```

### Enthalpy and Energy Flux

Recall this foreign concept from way long ago…

$$
H = \mathcal{E} + PV
$$

The reason we are bothering with this quantity is because it **sort of** appeared in our enery conservation equation:

$$
E+P =  \rho\left(\frac12 v^2 + \Phi + \underbrace{\mathcal{E}_{permass} + \frac{P}{\rho}}_\text{enthalpy per unit mass}\right)
$$

Note that $P/\rho = PV/m$ which allows us to recognize it as enthalpy per unit mass $h$. 

Now, we can write down an expression that we will call **energy flux**: 

$$
\text{Energy Flux} = \left(E+ P\right)\cdot \vec{v}
$$

Our expression above is thus:


$$
\boxed{\text{Energy Flux} = \rho\vec{v}\left(\frac12 v^2 + \Phi + h\right)} 
$$



### Executive Summary for Inviscid (non-viscous) Fluids



| Quantity | Density                                                          | Flux                                                                     | Conservation Equation for Quantity                                                                                                             |
|----------|------------------------------------------------------------------|--------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| Mass     | $\rho$                                                           | mass per time per area  $= \rho \vec{v}$                                | $\frac{\partial \rho}{\partial t} + \vec{\nabla}\cdot(\rho\vec{v}) = 0$ (Continuity Equation)                                                  |
| Momentum | $\rho \vec{v}$                                                   | $T_{ij} = P\delta_{ij} + \rho v_i v_j$                                  | $\frac{\partial}{\partial t} \left(\rho v_i \right) + \partial_j T_{ij} = -\rho \partial_i \Phi$ (Euler Equation)                              |
| Energy   | $E = \rho\left(\frac12 v^2 + \Phi + \mathcal{E}_{permass}\right)$| $\vec{f} = \rho\vec{v}\left(\frac12 v^2 + \Phi + h\right) = (E+P)\vec{v}$| $\frac{\partial E}{\partial t} + \vec{\nabla}\cdot \vec{f} = -\rho\dot{Q}_{cool} + \rho \frac{\partial \Phi}{\partial t}$ (Energy Conservation)|                                                                                                 |





## Example Simple Solutions: Hydrostatic Equilibrium, Polytropic Stars, and the Lane-Emden Equation


### Hydrostatic Equilibrium 

Let's start solving the three equations above! The most obvious first place to start is with hydrostatic equilibirum.

* Hydrostatic means that $\vec{v} = 0$. 
* Equilibrium means that $\frac{\partial}{\partial t} = 0$. 

Start with our three equations:

1\. Continuity Equation: Satisfied trivially: $0=0$

2\. Euler's Equation:

$$
\frac{\partial \vec{v}}{\partial t} + (\vec{v} \cdot \vec{\nabla})\vec{v} = -\frac{1}{\rho} \vec{\nabla}P - \vec{\nabla} \Phi \rightarrow \frac{1}{\rho}\vec{\nabla} P = -\vec{\nabla}\Phi
$$

3\. Poisson:

$$
\nabla^2 \Phi = 4\pi G \rho
$$


**Using $2$, $3$, and the Equation of State, should give us solutions!** Thus, the solution will depend on the equation of state.

#### Example 1: Atmosphere

Assume an isothermal equation of state for the atmosphere (approximately true for the lower stratosphere, about $15$ to $35$ kilometers up). Treating this as an ideal gas:

$$
P = nk_b T \rightarrow P = \frac{\rho}{\mu m_p} kT
$$


where $\mu$ is the mean molecular mass of our gas. Note the right side is a ton of constants since we have an isothermal atmosphere. Thus, $P = A\rho$ for some constatnt $A$. That is: $P\propto \rho$. Also note that:

$$
\mu \equiv 1 \text{ for hydrogen, } \equiv 16 \text{ for oxygen, and }  \approx 28.8 \text{ for air}
$$


Note that for the surface of a planet, we have $\vec\nabla \Phi = -\vec{g}$ which is constant near Earth's surface. 

Using this information, we have:

$$
\frac{1}{\rho} \vec\nabla P = -\vec\nabla \Phi \rightarrow \frac{A}{\rho} \vec\nabla \rho = -\vec{g}
$$

Let's choose $\vec g = -g \hat{z}$.

This gives:

$$
\frac{1}{\rho} \frac{\partial \rho }{\partial z} = -\frac{g}{A} = - \frac{\mu m_p g}{kT}
$$

This has a well-known solution!

$$
\boxed{\boxed{\rho(z) = \rho_0 e^{-\frac{z}{z_s}}} \text{ where } z_s \equiv \frac{kT}{\mu m_p g}}
$$

is the **exponentially stratified soluiton**. Putting in some numbers, we have:

* Atmosphere: $T \sim 300$ K $\boxed{\rightarrow z_s \approx 9}$ km. 
* At Mauna Kea, we have $z \sim 14000$ feet, which is about $z\sim 4.2$ km. This gives $\rho(z = 4.2 km) \approx 0.63 \rho(0)$.
    * The same is true for pressure since we assumed an equation of state of $P \propto \rho$. 


#### Example 2: Adiabatic Atmosphere

The adiabatic equation of state is different than an isothermal equation of state. The adiabatic approximation holds for the **troposphere** (see PS 1 in which we derive $\frac{dT}{dz}$). 



## Simple Solutions to the Fluid Equations


### Spherical Stars in Hydrostatic Equilibrium: The Lane-Emden Equation


We start with our equation for HE:

$$
\frac{1}{\rho} \vec\nabla P = -\vec\nabla \Phi
$$

We start with the standard parameterization, the **polytropic index** $n$:

$$
P = K \rho^{1+ \frac{1}{n}}
$$

Normally, lots of complications come into deriving $K$, so we will treat it as a constant for now.

#### Step 1

Solve HE equation, starting with the LHS:

$$
\frac{1}{\rho} \vec\nabla P = \frac{1}{\rho} \vec\nabla \left(K\rho^{1+\frac{1}{n}}\right)
$$

We will now define $q \equiv \rho^{1/n}$ for convenience. Using this:

$$
= \frac{1}{\rho}\vec\nabla\left(Kq^{n+1}\right) = \frac{n+1}{\rho} q^{n} \vec\nabla \left(Kq\right)
$$

Putting back in our $q$:


$$
= \left(n+1\right)\vec\nabla\left(K\rho^{1/n}\right)
$$

Now, the hydrostatic equilibrium equation becomes:

$$
\left(n+1\right)\vec\nabla\left(K\rho^{1/n}\right) = -\vec\nabla\Phi
$$

The solution to this equation:

$$
\rho = \left(\frac{\Phi_0 - \Phi}{\left(n+1\right)K}\right)^{n}
$$

where $\Phi=\Phi_0$ and $\rho=0$ at the surface. We also have the central boundary condition:

$$
\rho_c = \left(\frac{\Phi_0 - \Phi_c}{\left(n+1\right)K}\right)^{n}
$$



#### Step 2

Here, we add in the Poisson equation to solve for $\rho = \rho(r)$. After we have that, we have $\Phi(r)$ from the relation above and $P(r)$. 

To use the Poisson equation, let's re-write one more time:

$$
\rho = \rho_c \left(\frac{\Phi_0 - \Phi}{\Phi_0 - \Phi_c}\right)^{n}
$$

Notice that the term in parentheses is dimensionless! Let's start a new variable which will serve :

$$
\theta \equiv \frac{\Phi_0 - \Phi}{\Phi_0 - \Phi_c} = \left(\frac{\rho}{\rho_c}\right)^{1/n}
$$

With this definition, let's look at Possion's equation:

$$
\nabla^2 \Phi = 4\pi G \rho \rightarrow \nabla^2 \theta = -\frac{4\pi G \rho_c}{\Phi_0 - \Phi_c} \theta^n
$$

Let's impose spherical symmetry since we are dealing with spherical stars! This makes:

$$
\nabla^2 \theta = \frac{1}{r^2} \frac{1}{dr}\left(r^2 \frac{d\theta}{dr}\right)
$$

We will introduce another new variable, $\xi$, which will serve as a dimensionless radius:

$$
\xi \equiv \left(\frac{4\pi G \rho_c}{\Phi_0 - \Phi_c} \right)^{1/n} r
$$

We can get rid of the ugly denominator:

$$
\xi = \left(\frac{4\pi G}{(n+1)K} \rho_c^{1-1/n}\right)^{1/2} r
$$

Now back to Poisson, and we get the 

```{admonition} The Lane-Emden Equation

$$
\boxed{\frac{1}{\xi^2} \frac{d}{d\xi}\left(\xi^2 \frac{d\theta}{d\xi}\right) = -\theta^n}
$$

which depends on $n$ (the properties of the star). Note that this is second order, so we have two boundary conditions:

1\. At the star's center:

* $\xi \rightarrow 0$
* $\theta \rightarrow 1$ 
* $\frac{d\theta}{d\xi} = 0$ (zero force when the enclosed mass goes to $0$ as $r$ goes to $0$)
* EXCEPTION: When we have a central point mass, the differential boundary condition is a bit different, but we won't go down that route.

2\. At the star's surface:

* $\xi \rightarrow \xi_{max}$, which we can solve for
* $\theta \rightarrow 0$ 

```
Again, note that:

* $\xi \rightarrow r$
* $\theta \rightarrow \Phi \text{ or } r$

**Thus, if we solve this equation, we have our stellar structure!**

We are going to do one last variable change:

$$
\theta \rightarrow \chi \equiv \theta \xi 
$$

If we allow this, we get:

$$
\frac{d^2 \chi}{d \xi^2} = - \frac{\chi^n}{\xi^{n-1}}
$$


There are some analytic solutions to this equation for a few different $n$:

```{admonition} Case 1: $n=0$

See Problem Set 2. The gist:

This is the very incompressible limit, or basically when we have **solids**. This is the **stiffest** equation of state. Note that the other extreme is an isothermal sphere!

Solving for $\theta$ vs. $\xi$, we can also solve for $\xi_{max}$. 

```


```{admonition} Case 2: $n=1$

See Problem Set 2. The gist:

We have a different $\xi_{max}$ here, and thus we should find that, as $n$ increases, $\xi_{max}$ should also increase. Note that $n=1$ to about $n=1.5$ is a good approximation for fully convective stars. 

```


```{admonition} Case 3: $n=5$

When $n>5$, the energy is positive and we don't have a physical solution. Here, we have: $P \propto \rho^{6/5}$. Going through some mathematics, we get:

$$
\boxed{\theta(\xi) = \frac{1}{\sqrt{1+ \frac13 \xi^2}} = \left(\frac{\rho}{\rho_c}\right)^{1/5}}
$$

What are the boundary conditions here?

* At the center, $\xi \rightarrow 0$ and $\theta \rightarrow 1$. This checks out!
* At the surface, we have $\theta \rightarrow 0$ as $\xi \rightarrow \infty$. This gives our real density profile of:

$$
\frac{\rho}{\rho_c} = \frac{1}{(1+\frac13 \xi^2)^{5/2}} \propto r^{-5}
$$

Note that this profile is a **Plummer sphere**, which is well-studied and well-known. 

```

Note that, in general, the Lane-Emden equation can be solved numerically pretty easily. 


#### Mass-Radius Relation 


Recall our definitions of $\theta$ and $\xi$. For a fixed $K$, the value of the central desnity $\rho_c$ is what is setting the physical scale of the system/everything ($r$, $\rho$, etc). Consequently, we can see how our parameters scale with $\rho_c$, pulling out how mass depends on radius. 

We start at the star's surface:

$$
\theta = 0 \rightarrow \xi = \xi_{max} \rightarrow r = r_{max} = R_{star}
$$

We can now write down the star's mass:

$$
M = \int_0^{R} 4\pi \rho r^2  \, \mathrm{d}r
$$

Can we write this in terms of $\xi$ and $\theta?$ We can! Use the definitions from earlier.

$$
M = 4\pi \rho_c \left(\frac{4\pi G}{(n+1)K} \rho_c^{1-1/n}\right)^{-3/2} \int_0^{\xi_{max}} \underbrace{\theta^n \xi^2 \, \mathrm{d} \xi}_\text{fixed number for a given n}
$$

We now have:

$$
M \propto \rho_c^{1 - \frac32 + \frac{3}{2n}} \propto \rho_c^{\frac{1}{2}\left(\frac{3}{n}-1\right)}
$$

One last step – let's look at the star's radius:

$$
R = r_{max} \propto \rho_c^{\frac12 \left(\frac{1}{n}-1\right)}
$$

Thus, we have a relation between the mass and radius of a polytrope of index $n$:

$$
\boxed{M \propto R^{\frac{n-3}{n-1}}}
$$
##### A Famous Example 

When $n=\frac32$, the adiabatic index is $\gamma = 1 + 1/n = \frac53 \rightarrow P \propto \rho^{5/3}$. This is also the equation of state of non-degenerate stars! We also have:

$$
M \propto R^{-3}
$$

This is similar to the equation of state for a white dwarf. This is so weird! If we want **heavier** things, we need **smaller** volumes since mass is inversely proportionalt to the radius!

##### Another Famous Example

$n=0$ gives $M\propto R^{3}$ which is normal for solids/incompressible material sense. 




## Bernoulli's Theorem/Principle/Function/Equation

Let's start with Euler's equation:

$$
\frac{\partial \vec v}{\partial t} + \left(\vec v \cdot \vec\nabla\right) \vec v = -\frac{1}{\rho} \vec\nabla P - \vec\nabla \Phi
$$

Let's use a vector identity we have seen before:

$$
\left(\vec v \cdot \vec\nabla\right) \vec{v} = \frac12 \vec \nabla v^2 - \vec v \times \left(\vec \nabla \times \vec v\right)
$$

Why do we care about this? We can introduce the **vorticity**:

```{admonition} Vorticity

The vorticity $\vec \omega$ is:

$$
\vec \omega \equiv \vec \nabla \times \vec v
$$

```

We can now re-rwite our Euler equation and get **Equation (A)**:

$$
\frac{\partial \vec v}{\partial t} + \vec \nabla \left(\frac12 \vec v^2 + \Phi\right) + \frac{1}{\rho}\vec\nabla P - \vec v \times \vec \omega = 0
$$



We have two special cases of interest:

1\. **Steady-flow Limit**

This means that $\partial_t (\text{everything}) = 0$. We also are dealing with "ideal" fluids, meaning we ignore dissipation. In this case, **entropy is constant along flows.**

We will now do something a bit strange, but we will dot $\vec{v}$ into equation (A), which will allow us to throw out the vorticity piece. In this case, this equation becomes:

$$
\vec v \cdot \vec \nabla\left(\frac12 v^2 + \Phi\right) + \frac{1}{\rho}\left(\vec v \cdot \vec \nabla\right)P = 0
$$

We would **love** to put everything in one parentheses, but we need a bit of help. **Anytime we get stuck, just use enthalpy.**\

Recall that **enthalpy:**

$$
H = \mathcal{E} + PV
$$

We had the per-mass version as well:

$$
h = \epsilon + \frac{P}{\rho}
$$

This gives 

$$
dh = d\epsilon + P d(\frac{1}{\rho}) + \frac{1}{\rho} dP
$$

From the First Law, we have $d\epsilon = T \mathrm{d}S - P \,\mathrm{d}\left(\frac{1}{\rho}\right)$. This gives:

$$
dh = T\mathrm{d}S + \frac{1}{\rho} \mathrm{d}P
$$

For ideal flow $dS = 0$, we have:

$$
\vec \nabla h = \frac{1}{\rho}\vec\nabla P \text{ for constant S, i.e., ideal fluids}
$$

Returning to our equation above:

$$
\vec v \cdot \vec \nabla \left(\frac12 v^2 + \Phi + h \right) 0
$$

This gives our **Bernoulli Function**:


```{admonition} Bernoulli Function 

\mathcal{B} \equiv \frac12 v^2 + \Phi + h = \frac12 v^2 + \Phi + \epsilon + \frac{P}{\rho}

```

Thus:

$$
\vec v \cdot \vec \nabla \mathcal{B} = 0 = \frac{D\mathcal{B}}{Dt} 
$$

Thus:

$$
\mathcal{B} = \text{constant along fluid flow}
$$

Recall energy flux $\vec{f}$ from last time. It turns out that:

$$
\vec{f} = \mathcal{B}\rho \vec{v}
$$

So nothing is new!


---


2\. **If flow is also irrotational in addition to steady-flow**


This case means that $\vec w = \vec \nabla \times \vec v = 0$. Thus, we don't have to do the weird $\vec v$ dotted throughout the entire equation since the voricity term is already $0$. This gives:

$$
\vec \nabla \mathcal{B} = 0
$$

Thus $\mathcal{B}$ is constant **everywhere**, not just **along the fluid flow**. 

---


##### A Comment: Vorticity is Conserved

In general, 

* Euler Equation $\rightarrow \frac{\partial \vec v}{\partial t} + \vec \nabla \mathcal{B} - \vec v \times \vec \omega = 0$.
* We can take the curl of this above equation. If we do this, we get an equation for the vorticity:

$$
\boxed{\frac{\partial \vec \omega}{\partial t} = \vec \nabla \times \left(\vec v \times \vec \omega\right)}
$$

