# Fluid Instabilities

## Gravitational Instabilities in a Static vs. Expanding Medium

Let's recall two of the dispersion relations we have derived:

```{admonition} Free Wave Dispersion Relation: Sound Waves

$$
\omega = v_s k 
$$

```

```{admonition} Surface Water Waves

Here, we had gravity (constant), which gives a dispersive relation:

$$
\omega^2 = gk\tanh(kH)
$$

where $H$ is the depth of the sea. Also note that here, we had $\vec \nabla \Phi = -\vec g$. 

```

And also, recall our **equations for linear perturbation theory**:

$$
\rho = \rho_0 + \rho_1
$$
$$
P = P_0 + P_1
$$
$$
\vec v = \vec v_0 + \vec v_1
$$
$$
\Phi = \Phi_0 + \Phi_1
$$

Note that $\rho_1 \ll \rho_0$, and so forth. We also had things like the **adiabatic sound speed**:

$$
v_s^2 = \left(\frac{\partial P}{\partial \rho}\right)_\text{const. S} = \frac{P_1}{\rho_1}
$$


### Static, Uniform Medium 

For a static, uniform medium, we have $\rho_0 = \text{const.}$, $P_0 = \text{constant}$, and $\vec v_0 = 0$. The potential is interesting, though, which we will return to. The fluid equations are:


```{admonition} Zeroth Order Continuity Equation

$$
\frac{\partial \rho_0}{\partial t}  + \vec \nabla (\rho_0 \vec v_0) = 0
$$

This is trivially true. 

```


```{admonition} Zeroth Order Euler Equation

The LHS is $0$ since $\vec v_0 = 0$. The RHS of the Euler equation tells us that:

$$
-\frac{1}{\rho_0} \vec \nabla  P_0 - \vec \nabla \Phi_0 = 0 \rightarrow \vec \nabla \Phi_0 = 0
$$

```


```{admonition} Zeroth Poisson Equation

We have:

$$
\nabla^2 \Phi_0 = 4\pi G \rho_0 
$$

Since we are radially symmetric, we have:

$$
\vec \nabla \Phi_0 = \frac{4\pi}{3} G\rho_0 \vec{r}

$$

```

**Hey! Wait a minute! The two zeroth order equations tell us that $\rho_0$ has to be 0. This isconsistency is actually called the Jeans-Swindle.** The reason we have an inconsistency is because we need our medium to be infinitely large. Thus, the Jean's Swindle is a reflection of the unrealistic background we are considering. 


We now go to the perturbed equations:


```{admonition} First Order Continuity

$$
\frac{\partial \rho_1}{\partial t} + \rho_0 \vec \nabla \cdot \vec v = 0
$$

```

```{admonition} First Order Euler

$$
\frac{\partial \vec v_1}{ \partial t} = - \frac{v_s^2}{\rho_0} \vec \nabla P_1 - \vec \nabla \Phi_1
$$

```


```{admonition} First Order Poisson

$$
\nabla^2 \Phi_1 = 4\pi G \rho_1
$$

```

We can combine the first two equations, taking the time derivative of the first. Doing so, we get:

$$
\frac{\partial^2 \rho_1 }{\partial t^2} + \rho_0 \left(-\frac{v_s^2}{\rho_0} \nabla^2 \rho_1 - \nabla^2 \Phi_1\right) = 0
$$

Now use the Poisson equation (equation 3), to give a **wave's equation with a driving term:**

$$
\boxed{\frac{\partial^2 \rho_1}{\partial t^2} - v_s^2 \nabla^2 \rho_1 - 4\pi G\rho_0 \rho_1 = 0}
$$

We use Fourier analysis, turning a differential into algebraic equation, since the modes decouple. We do this by saying $\rho(\vec r, t) \propto \int e^{i (\vec k \cdot \vec r - \omega t)} \, c(\vec{k}) \, d^3 k$ . However, if we had non-linear terms like $\rho_1^2$, all Hell breaks loose in Fourier space. This is because we have convolutions when things are non-linear, and that is ugly. 

Anyways, we get:

$$
-\omega^2 + v_s^2 k^2 - 4\pi G\rho_0 = 0 
$$

```{admonition} Dispersion Relation for Jean's Instability
$$
\boxed{\omega^2 = v_s^2 k^2 - 4\pi G \rho_0}
$$
This is a dispersive wave (since we are non-linear in $k$). We can also immediately see that $\omega$ might be imaginary! If pressure wins, we have waves/oscillatory behavior! If gravity wins, we get exponential collapse.

We can write this in a bit different way:

$$
\omega^2 = v_s^2 \left(k^2 - k_J^2\right)
$$

where:

$$
k_J \equiv \sqrt{\frac{4\pi G \rho_0}{v_s^2}}
$$

is the **Jean's wavenumber**. We also often see:

$$
\lambda_J \equiv \frac{2\pi}{k_J}
$$

And Jean's mass (the mass enclosed within $\lambda_J$):

$$
M_J = \frac{4\pi}{3} \lambda_J^3 \rho_0
$$

And we often say things like ``what is the Jean's mass/Jean's length at a time in cosmic history?'' Here, we compare the density to the sound speed, more or less, through the definition of Jean's wavenumber. 

Note that pre-CMB, the Jean's Length is huge. After free electrons combine with ionized hydrogen (forming neutral hydrogen), photons free stream. Thus, the Jean's Mass drops tremendously. The Jean's Mass post-recombination is of order $10^{6}$ solar masses. **This is when structure formation takes off!**



```

#### Two Regimes

##### Regime A

We consider here $k > k_J$ or $\lambda < \lambda_J$. In this case, we have $\omega^2 > 0$, and thus $\omega$ is real. $\rho_1$ oscillates like sound waves. This is a **stable solution**. 

##### Regime B

Here $\omega^2<0$, and thus $\omega$ is imaginary. This implies:

$$
\rho_1 \propto e^{\pm |\omega| t}
$$

**The growing solution is exponential!**


#### An Side

Note that the dispersion relation for Jean's instability is very similar to the **plasma frequency**:

$$
\omega^2 = v_s^2 k^2 + \frac{4\pi n_e e^2}{m_e} > 0
$$

Thus the plasma frequency is always oscillatory!


### An Expanding Medium

In this case, we have:

$$
\rho_0 = \rho_0(t)
$$

We can define a $\delta$ such that:

$$
\delta \equiv \frac{\rho_1}{\rho_0} = \frac{\rho - \rho_0}{\rho_0} = \left(\delta \rho\right)
$$
The overdensity can be as large as can be, but the underdensity can only get as negative as $-1$. This negative overdensity regions of the Universe are called **voids**. Thus $(-1 \leq \delta < \infty)$. 

Also note that our fluid velocity is no longer $0$. Instead, we have $\vec v_0 = H \vec r$ (Hubble expansion). This is also $\vec v = \frac{\dot{a}}{a}\vec r$. By convection, we choose $a=1$ today, and $a<1$ before today. Note that taking:

$$
\vec \nabla \cdot \vec v_0 = 3 \frac{\dot{a}}{a}
$$
And note that 

$$
\vec{v}_1 = \text{ peculiar velocity}
$$

We now go to our fluid equations:

```{admonition} Zeroth Order Continuity

$$
\frac{\partial \rho_0}{\partial t} + \rho_0 \vec \nabla \cdot \vec v_0 = \frac{\partial \rho_0}{\partial t} + \frac{3\dot{a}}{a} \rho_0 = 0 \rightarrow \rho_0(t) \propto \frac{1}{a(t)^3} \propto \frac{1}{\text{volume}}
$$

This is nice and in accordance with our intuition.


```

```{admonition} First Order Continuity


$$
\frac{\partial \rho_1}{\partial t} + \rho_0 \vec \nabla \cdot \vec v + \vec \nabla (\rho_1 \vec v) = 0 
$$

```

We'll now want to go to $\delta$ coordinates in our first order continuity equation:

$$
\rho_1 = \rho_0 \delta \rightarrow \rho_0 \dot{\delta}  +\delta \dot{\rho}_0 + \rho_0 \vec \nabla \cdot \vec v_1 + \rho_0 \vec v_0 \cdot \vec \nabla \delta + \rho_0 \delta \vec \nabla \cdot \vec v = 0 
$$

Also note that $\dot{\rho}_0 = -3\frac{\dot{a}}{a}$ from the continuity equation, and we know that $\vec \nabla \cdot \vec v_0 = 3\frac{\dot{a}}{a}$. This cancels nicely:


Dividing through by $\rho_0$, we get the **linearized Continuity Equation for an expanding Universe**:

$$
\dot \delta + \vec \nabla \cdot \vec v_1 + \frac{\dot a}{a} \rho_0 \vec r\cdot \vec \nabla \delta = 0
$$
where we have replace $v_0$ with Hubble's Law. 


```{admonition} Zeroth Order Euler Equation

Again, $\vec v_0$ is not zero, and so we just get a constra:

$$
\frac{\partital \vec v_0}{\partial t} + (\vec v_) \cdot \vec \nabla) \vec v_0 = - \vec \nabla \Phi_0
$$

```


```{admonition} First Order Euler Equation

$$
\frac{\partial \vec v_1}{\partial t} + (\vec v_0 \cdot \vec \nabla) + (\vec v_1 \cdot \vec \nabla) \vec v_0 = -\frac{v_s^2}{\rho_0} \vec \nabla \rho_1 - \vec \nabla \Phi_1
$$

```

Let's simplify the ugly term:

$$
(\vec v_1 \cdot \vec \nabla) \vec v_0 = \frac{\dot a}{a} (\vec v_1 \cdot \vec \nabla) \vec r
$$

And note that:

$$
\vec v_1 \cdot \vec \nabla = v_{1x} \partial_x + v_{1y} \partial_y + v_{1z} \partial_z 
$$

And so acting on $\vec{r}$, we get: $(\vec v_1 \cdot \vec \nabla) \vec r = \frac{\dot a}{a} \vec{v}_1$. 

This makes our First Order Euler equation;

$$
\frac{\partial v_1}{\partial t} + \frac{\dot{a}}{a}(\vec r \cdot \vec \nabla) \vec v_1 + \frac{\dot a}{a} \vec v_1 = -v_s^2 \vec \nabla \delta - \vec \nabla \Phi_1
$$

And finally, our Poisson:

```{admonition} Zeroth and First Order Poission


We get:

$$
\nabla^2 \Phi_0 = 4\pi G \rho_0
$$

$$
\nabla^2 \Phi_1 = 4\pi G \rho_0 \delta
$$

```


We no longer have Jean's Swingle, by the way! 









