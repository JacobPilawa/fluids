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

