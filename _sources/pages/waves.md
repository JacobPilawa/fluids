# Waves

We will now begin to consider perturbations to our equations. Here, we consider small, stable perturbations. The standard recipe is to break our fluid properties $(\vec v, \rho, P, \Phi, \cdots)$ into $0th$ order $+ 1$st order pieces. We will assume that the first order pieces are $\ll$ than the $0$th order pieces. The word for this is **linear perturbation theory.** 

Here is a note on notation. We will have something like:

$$
\vec v = \vec v_0 + \vec v_1 
$$

where the subscript refers to the order, i.e., $\vec v_1 \ll \vec v_0$. This means:

* $\vec v = \vec v_0 + \vec v_1$ 
* $P = P_0 + P_1$
* $\rho = \rho_0 + \rho_1$
* $\Phi = \Phi_0 + \Phi_1$


```{note}

The thermal behavior of the perturbations $P_1$, $\rho_1$ need to behave the same way was the $0$th order counterpart. An example is the equation of state -- an atmosphere might be isothermal, but the perturbations can be adiabatic.

```


## Sound Waves: The Simplest Case

Consider a static, uniform (unperturbed) medium. We will ignore gravity. Thus, all we have is pressure for the physics. 

In this case, 

$$
\vec v = \vec v_1
$$

$$
P = \underbrace{P_0}_\text{constant} + P_1
$$

$$
\rho = \underbrace{\rho_0}_\text{constant} + \rho_1
$$

$$
\Phi = 0
$$


We now plug these into our fluid equations. 

### Zeroth Order Equations

The $0$th order fluid equations are:

```{admonition} The Continuity Equation

$$
\frac{\partial \rho}{\partial t} + \vec \nabla \cdot \left(\rho \vec v_0\right) =0 
$$

This is satisfied trivially. This tells us nothing.

```


```{admonition} Euler Equation


$$
\underbrace{\frac{\partial \vec v_0}{\partial t} + \cdots }_{=0} = -\frac{1}{\rho_0}\vec \nabla P_0 = 0
$$

This is also satisfied trivially.

```

### First Order Equations

```{admonition} Continuity Equation

$$
\frac{\partial \rho_1}{\partial t} + \left(\rho_0 \vec \nabla \cdot \vec v_1\right) = 0
$$

```

```{admonition} Euler Equation

$$
\frac{\partial \vec v_1}{\partial t} = -\frac{1}{\rho_0}\vec \nabla P_1
$$

Note that the advection term is $0$ to first order.
```

This is simply two coupled equations which we can solve! But, before that, we will introduce a new quantity, the **sound speed** $v_s$.

```{admonition} Sound Speed

$$
v_s^2 = \frac{\partial P}{\partial \rho} = \frac{P_1}{\rho_1}
$$

where this measures how pressure changes with density. 

```

Combining the continuity and the euler equation together by taking the time derivative of the first equation:

$$
\rightarrow \frac{\partial^2 \rho_1}{\partial t^2} - \nabla^2 P_1 = \boxed{\frac{\partial \rho_1}{\partial t^2} - v_s^2 \nabla^2 \rho_1 =0 }
$$

where we have assumed that the sound speed is a constant. This is a trivial waves equation! We have solved this in our childhood:

$$
\rho_1(\vec r,t) = \int \mathrm{d}^3 k \, e^{i\left(\vec k \cdot \vec r - \omega t\right)}\rho_1(\vec k)
$$

The solution is thus just a relationship between $k$ and $\omega$. This gives **a dispersion relation for a free wave**:

$$
-\omega^2 + v_s^2  k^2 = 0 \rightarrow \boxed{\omega^2 = v_s^2 k^2}
$$

For completeness, we have:

```{admonition} The Group Velocity

v_g \equiv \frac{\partial \omega}{\partial k} = v_s
```

```{admonition} The Phase Velocity

v_{phase} \equiv \frac{\omega}{k} = v_s
```

For sound waves, these are independent of the wavenumber $k$. When this is the case, we say we have **"non-dispersive waves."**

#### What about perturbed fluid velocities/other quantities?

We can use our solution for $\rho$ and the Euler Equation above to get:

$$
\frac{\partial \vec v}{\partial t} = -\frac{v_s^2}{\rho_0} \vec \nabla \rho_1 \rightarrow \text{ Fourier } \rightarrow \frac{-v_s^2}{\rho_0}\left(i \vec{k} \right)\rho_1
$$

We can show that:

$$
\vec v_1 = \frac{v_s^2}{\rho_0}\frac{\vec k}{\omega}\rho_0 = \frac{\omega}{k} \hat{k} \frac{\rho_1}{\rho_0}
$$

Note that the perturb quantites $\vec v_1, \rho,$ and $P$ are all **in phase**. 

##### Fourier Transforms and Conceptual Review

Note that FTs are nice since we term finite difference problems into algebraic problems. This is awesome numerically!



We have some density perturbation. This gives us a pressure gradient and thus a force. This force accelerates the fluid element. This perturbed velocity further induces a density perturbation, leading to sound wave propagation! 



##### Some Numbers and Notes About Sound Speed

```{admonition} Isothermal Sound Speed

Isothermal Sound Speed:

$$
v_s^2 = \left(\frac{\partial P}{\partial \rho}\right)_T
$$

Remember that the ideal gas has: $P = \frac{\rho}{\mu m_p} k_b T$. This makes:

$$
\boxed{v_s = \sqrt{\frac{k_b T}{\mu m_p}}}
$$

```

```{admonition} Adiabatic Sound Speed 


$$
v_s^2 \equiv \left(\frac{\partial P}{\partial \rho}\right)_S
$$

The adiabatic ideal gas has $P = \kappa \rho^\gamma$. Taking the derivative, we have:

$$
v_s^2 = \gamma \frac{P}{\rho} = \gamma \frac{k_b T}{\mu m_p}
$$

This gives:

$$
v_s = \sqrt{\gamma\frac{k_b T}{\mu m_p}} = \sqrt{gamma} v_s^\text{isothermal}
$$

```

Which one of these speeds are relevant? 


###### Examples of Air Sound Speed

* Adiabatic: (A useful thing to know: $k_b T \sim \frac{1}{40} \text{ eV}$ at room temperature air)
    * Has $v_s^\text{adiabatic} = \sqrt{\frac{7}{5}\frac{1/40 \text{ eV}}{28.8 \cdot 10^{9} \text{ eV }}} \cdot c \sim 330 \text{ m/s}$ 
* Isothermal:
    * Has $v_s^\text{isothermal} \sim 280 \text{ m/s}$. 

The data is closer to the adiabatic case. 


###### Examples of Water Sound Speed

* This is closer to $v_s \sim 1500 \text{ m/s}$ ! 


###### Examples of Sound Speed in Iron

* This is closer to $v_s \sim 5 \text{ km/s}$. 


## Gravity Waves

Let's look at water waves on the surface of Earth with the same spirit as in sound waves. 



```{image} ../figures/fig7.png
:alt: fig7
:width: 600px
:align: center
```



Consider a single fluid of constant density $\rho_0$ in equilibrium ($\vec v_0 = \vec 0$. ) This means that the Euler Equation is:

$$
\frac{1}{\rho_0}\vec \nabla P = - \vec \nabla \Phi_0 = \vec g
$$

Thus:

$$
\frac{1}{\rho_0} \frac{\partial P_0}{\partial z} = - g \rightarrow P_0 = -\rho_0 g z + \text{ constant}
$$



### Perturbed Equations

We have $\vec v = \vec v_0 + \vec v_1 = \vec v_1$, $P = P_0 + P_1$, $\rho = \rho_0 = \text{ constant, incompressible}$, and $\rho_1 = 0$ since it is incompressible. Note that $\vec \nabla \Phi = - \vec g$ due to the external gravitational field of Earth. $\Phi_1 = 0$ means that the self-gravity of the water is negligible. The linearized, 1st order fluid equations are thus:


```{admonition} Continuity Equation 

Remember from before that the incompressible condition implies:

$$
\vec \nabla \cdot \vec v_1 = 0
$$

Note we chose our coodinates (considering waves travelling along $x$-axis) such that this equation is:

$$
\frac{\partial}{\partial x} v_{1x} + \frac{\partial}{\partial z} v_{1z} = 0$. 
$$

```

```{admonition} Euler Equation}

We have:

$$
\frac{\partial \vec v_1}{\partial t} = \frac{1}{\rho_0}\vec\nabla P_1
$$

Let's write out the components:

$$
\frac{\partial}{\partial t} v_{1x} = -\frac{1}{\rho_0}\frac{\partial }{\partial x} P_1
$$

$$
\frac{\partial}{\partial t} v_{1z} = -\frac{1}{\rho_0}\frac{\partial }{\partial z} P_1
$$

```

We can choose to solve for $P$ or $\vec v$, and we choose $P$ first. We can use the equation from the Contunity Equation (by take the partial derivative) to get:

$$
0 = \frac{\partial}{\partial t} \left(\frac{\partial v_{1x}}{\partial t} + \frac{\partial v_{1z}}{\partial t}\right) = -\frac{1}{\rho_0} \left(\frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial z^2}\right) P_1
$$

This is:

$$
\left(\frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial z^2}\right)P_1 = 0
$$

This is a Laplace Equation in $2D$. This has solutions! Because we are looking for waves along $x$, we have the ansatz:

$$
P_1(x,z,t) \propto e^{i\left(k \cdot x - \omega t\right)} \cdot \mathcal{f}(z)
$$
Plug this into the Laplace Equation, and we get:

$$
-k^2 \mathcal{f} + \frac{\partial f}{\partial z^2} = 0 \rightarrow \mathcal{f}(z) \propto e^{\pm kz}
$$

All the action will now come from the boundary conditions. We can write:

$$
P_1(x,z,t) = Ae^{i(kx - \omega t)}\left(e^{kz} + Be^{-kz}\right)
$$
$$
v_{1z} (x,z,t) = \frac{Ak}{\rho_0 i\omega}e^{i\left(kx-\omega t\right)}\left(e^{kz}-Be^{-kz}\right)
$$

where the second equation for $v_{1z}$ comes from the 2nd Euler Equation above and where we have gone into Fourier Space. 


#### Boundary Conditions

1\. $z=-H$, the bottom of the sea. Here, we have:

$$
v_{1z}(z=-H) = 0
$$

This condition implies that $\boxed{B \rightarrow e^{-2kH}}$. Immediately, we have:


$$
P_1(x,z,t) = Ae^{i(kx - \omega t)}e^{-kH}\left(2 \cosh\left[k(z+H)\right]\right)
$$
Similarly, 

$$
v_{1z} = \frac{Ak}{\rho_0 i \omega } e^{i(kx-\omega t)} e^{-kH} \cdot 2 \sinh (k(z+H))
$$

2\. At the surface of the (free aka no force) air-water interface (z=0 for our coordinates). Let's introduce the **fluid displacement vector** $\vec \xi(\vec r, t)$ defined such that:

$$
\frac{d\vec \xi}{d t} \equiv \vec v
$$



The vertical displacement is thus:

$$
\frac{d\xi_z}{dt} = v_{1z} \propto e^{i\omega t} \rightarrow \xi_z = \frac{v_{1z}}{-i \omega} 
$$

which we actually hav aen equation for in 1\. . 

Note that saying we have a "free air water interface" is the same as saying we have "constant pressure along fluid element." This translates to a condition:

$$
P_1 + \vec \xi \cdot \vec \nabla P_0 = 0 \text{ if surface tension is unimportant}
$$

We will see this next time. 
