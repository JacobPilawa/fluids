# Magnetohydrodynamics (MHD)

Magnetohydrodynamics describes the dynamics of electrically conducting fluids in the presence of a magnetic field $\vec B$. The basic process that we are examining is:

* The $\vec B$ field idnuces currents in a moving, conducting fluid. The current in turn creates forces on the fluid, and also changes the $\vec B$ field. We add some aditional terms to the Navier-Stokes equation, and we couple those terms with Maxwell's Equations.


## Maxwell's Equations

```{admonition} Maxwell Equations

$$
\vec \nabla \cdot \vec E = 4\pi \rho_e \text{ Coulomb's Law}
$$

* $\rho_e$ is charge density.

$$
\vec \nabla \cdot \vec B = 0
$$

$$
\vec \nabla \times \vec E = \frac{1}{c}\frac{\partial \vec B}{\parital t} \text{ Faraday's Law of Induction}
$$

* a time-varying $\vec B$ induces an electric field. 

$$
\vec \nabla \times \vec B = \frac{4\pi}{c}\vec{J} + \underbrace{\frac{1}{c}\frac{\partial \vec E}{\partial t}}_\text{displacement current} \text{ Ampere's Law }
$$

* $\vec{J}$ is the current density

```


### Some Comments

* **Units:** 
    * Gaussian
        * This is what we use. 
        * $E$ and $B$ are in the same units here. 
    * SI
        * $[E] \sim [v\cdot B]$ 

* Charge and Current Densities
    * $\rho_e \sim \frac{\text{charge}}{\text{volume}}$ 
    * $\vec J \sim \frac{\text{charge}}{\text{volume}} \vec v = \rho_e \vec u$ where $\vec u$ is the electron velocity.


* Combining Maxwell's Equations:
    * Let's combine Coulomb's Law + Ampere's law by taking the divergence of Ampere's Law:

$$
\vec \nabla \cdot (\vec \nabla \times \vec B) = 0 = \frac{4\pi}{c} \vec \nabla \cdot \vec J + \frac{1}{c}\frac{\partial}{\partial t} \left(\underbrace{\vec \nabla \cdot \vec E}_{4\pi \rho_e}\right)
$$

And thus we get charge conservation! ($\vec J = \rho_e \vec u$)

$$
\boxed{\frac{\partial \rho_e}{\partial t} + \vec \nabla \cdot \vec J = 0}
$$

* For steady-state current ($\partial_t \rho_e =0$, $\partial_t \vec E = 0$), then $\vec \nabla \cdot \vec J =0$. 
    * We also have that Ampere's Law becomes:

$$
\vec \nabla \times \vec B = \frac{4\pi}{c}\vec J 
$$

Taking the divergence:

$$
\vec \nabla \cdot \vec J = 0
$$
which is consistent with what we had before. Here's the important part: **Maxwell realized that, without the displacement current term, we would only be allowed to have steady-state field (time variation not allowed)**. 


* In the absence of sources for $\vec J$, Ampere's law becomes:

$$
\vec \nabla \times \vec B = \frac{1}{c}\frac{\partial \vec E}{\partial t}
$$

Let's take the curl:

$$
\vec \nabla \times \left( \vec \nabla \times \vec B\right) = \frac{1}{c}\frac{\partial }{\partial t}\left(\vec \nabla \times \vec E\right) = -\frac{1}{c^2}\frac{\partial^2 \vec B}{\partial t^2}
$$

Using vector identities:

$$
-\nabla^2 \vec B + \vec \nabla(\underbrace{\vec\nabla\cdot\vec B}_{=0}) =  -\frac{1}{c^2}\frac{\partial^2 \vec B}{\partial t^2}
$$

And thus:

$$
\boxed{\left(\nabla^2 - \frac{1}{c^2}\frac{\partial^2}{\partial t^2}\right)\vec B = 0}
$$

We get a wave equation! And we get the same for a $\vec E$ field as well. 


## Ohm's Law and Induction Equation for the Magnetic Field

Ohm's Law is an empirical law, describing the relation between electric current and electric field (the Engineer's Version):

$$
I = \frac{V}{R}
$$

This often fails at high $\vec E$. 

1\. In the rest frame of the conducting material: $\vec J^\prime = \sigma \vec E^{\prime}$, where $\prime$ denotes we are in the rest frame. Here, $\sigma$ is the electric conductivity, with units of $\frac{1}{\text{time}}$. We have:

$$
J \sim \frac{1}{A}, E\sim \frac{V}{L} \rightarrow \text{ Ohm's Law: } \frac{I}{A} \sim \sigma \frac{V}{L} \rightarrow V \sim \frac{L}{A\sigma}I \equiv RI
$$

Thus:

$$
\sigma = \frac{L}{A\sigma} \rightarrow R \sim \frac{L}{A\sigma} \sigma \frac{1}{L\sigma} \propto \frac{1}{\sigma}
$$
Resistance is inversely propotional to conductivity.

2\. In the lab frame (an intertial frame), the conductor is moving at $\vec v$. We will show that, in this case, 

$$
\vec J = \sigma \left(\vec E + \vec v\times \frac{\vec B}{c}\right)
$$
For a **perfect conductor**, meaning that $\sigma \rightarrow \infty$, we have:

$$
\vec E + \vec v \times \frac{\vec B}{c} = 0 \rightarrow \vec E \perp \vec B
$$

We also have:

$$
|\vec E | \sim \frac{v}{c}|\vec B| \ll |\vec B|
$$
We now have three equations (Ohm's Law, Faraday's Law, Ampere's Law) and three unknown vector fields ($\vec B, \vec E, \vec J$). We combine these equations to get a single equation for $\vec B$, giving **the induction equation.**

Start with Ohm's Law:

$$
\vec E = \frac{\vec J}{\sigma} - \frac{\vec v \times \vec B}{c} \underbrace{\rightarrow}_\text{Ampere + ignore displacement current} \frac{c}{4\pi \sigma}\vec \nabla \times \vec B - \frac{\vec v \times \vec B}{c}
$$

We now use Faraday's Law:

$$
\frac{\partial \vec B}{\partial t} + c \vec \nabla \times \vec E = 0 
$$

We now have:

$$
\frac{\partial \vec B}{\partial t} + \frac{c^2}{4\pi \sigma}\vec v \times \left(\vec \nabla \times \vec B\right) - \vec \nabla \times (\vec v \times \vec B) = 0 \text{ assuming that } \sigma \text{ is spatially constant}
$$

Last time, we looked at $\vec \nabla \times (\vec \nabla \times \vec B) = -\nabla^2 \vec B + \vec \nabla (\underbrace{\vec \nabla \cdot \vec B}_{0})$ 

And thus gives:

```{admonition} The Induction Equation -- the evolution equation for B fields

$$
\boxed{\frac{\partial \vec B}{\partial t} = \vec \nabla \times \left(\vec v \times \vec B\right) + \eta \nabla^2 \vec B}
$$

where 

$$
\eta \equiv \frac{c^2}{4\pi \sigma}
$$

is the "magnetic diffusivity" which is proportional to resistance.

```

This equation above is similar to the NS equation, by the way! And it motivates the introduction of the **magnetic Reynold's number.** First, recall the hydrodynamical Reynold's number:

$$
\mathcal{Re} = \frac{vL}{\nu}
$$

Similarly,we can define:

$$
\mathcal{Re}_{m} \sim \frac{|\vec \nabla \times (\vec v\times \vec B)|}{|\eta \nabla^2 \vec B|}
$$
Dimensionally, we have:


$$
\mathcal{Re}_{m} \sim\frac{vB/L}{\eta B/L^2} \sim \frac{vL}{\eta}
$$
where $v$ is the velocity, $L$ is the lenght of a typical variation of $\vec B$, and $\eta$ is the magnetic diffusivity/magnetic resistance. 

We thus have two regimes, the low and high (magnetic) Reynold's number regions:

**1\. Low $\mathcal{Re}_{m}$ has diffusion dominating:**

$$
\frac{\partial \vec B}{\partial t} \approx \eta \nabla^2 \vec B
$$

And we can estimate the timescale for field decay due to diffusion:

$$
\frac{B}{\tau} \sim \frac{\eta B}{L^2} \rightarrow \tau \sim \frac{L^2}{\eta}
$$


**2\. Convective term dominates**: this happens when we have really large conductivity (no resistance). This is the **ideal MHD limit.** Many astrophysical systems are well-described in this regime.

$$
\frac{\partial \vec B}{\partial t} \approx \vec \nabla \times (\vec v\times \vec B)
$$

