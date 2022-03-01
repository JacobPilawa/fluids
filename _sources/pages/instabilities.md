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
\dot \delta + \vec \nabla \cdot \vec v_1 + \frac{\dot a}{a} \vec r\cdot \vec \nabla \delta = 0
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




---


Here, we continue from last week. Let's recall a few things:

#### Static Case: Pressure vs. Gravity

In this case, we derived:

$$
\omega^2 = v_s^2 k ^2 - 4\pi G \rho_0
$$

or 

$$
\omega^2 = v_s^2 \left(k^2 - k_J^2\right)
$$

where $k_J$ is the **Jeans Wavenumber**, defined as:

$$
k_J \equiv \sqrt{\frac{4\pi G\rho_0}{v_s^2}}
$$

We got this by perturbing our fluid equations in the limit where the sub-0 pieces do not depend on time, nor space. We then moved into the contracting or expanding medium.


### Expanding Case

The linearized fluid equations were dervied last time. These were:


From the continuity equation:
$$
\dot{\delta} + \vec \nabla \cdot \vec v_1 + \frac{\dot a}{a}\left(\vec r \cdot \vec \nabla\right) \delta = 0
$$


From the Euler equation:

$$
\frac{\partial \vec v_1}{\partial t} + \frac{\dot a}{a}\left(\vec r \cdot \vec \nabla\right)\vec v_1 + \frac{\dot a}{a} \vec v_1 = -v_s^2 \vec \nabla \delta - \vec \nabla \Phi
$$

Note that we might have had this expression wrong last time. We had an extra $\rho_0$ somewhere.

And from the Poisson equation:

$$
\nabla^2 \Phi_1 = 4\pi G \rho_0 \delta
$$

To solve these equations, we go into Fourier space. Also, we will go into the co-moving coordinate system which will cancel out many of the terms. First, doing the Fourier Transform:

To go to co-moving coordinates:

$$
\vec r = a(t) \vec x 
$$

where $\vec r$ is physical and $\vec x$ are the co-moving coordinates. Note that $a(\text{today}) = 1$. Correpsondingly, our co-moving wave number $\vec k$ will be paried with $\vec x$ and not $\vec r$. Go to Fourier Space:

$$
\delta(\vec r, t) 
$$

$$
\vec v_1 (\vec r, t)
$$

$$
\Phi_1(\vec r, t)
$$

These three quanities are:

$$
= \int \mathrm{d}^3 \, k \, e^{i\frac{\vec k \cdot \vec r}{a(t)}} f_k(t)
$$

where $f_k(t)$ are the Fourier transformed functions. In one shot, we will do a lot of algebra here. We will calculate $\dot{\delta}$ in real space:




$$
\dot \delta(\vec r, t) = \int d^3\,k\, e^{i\frac{\vec k \cdot \vec r}{a(t)}} \left(\dot{\delta}_k - \frac{\dot a}{a} i \frac{\vec k \cdot \vec r}{a(t)} \delta_k\right)
$$




And 

$$
\vec \nabla \delta(\vec r, t) =  \cdots \frac{i \vec k}{a(t)}\delta_k
$$
And 

$$
\vec \nabla \cdot \vec v_1(\vec r,t) = \cdots i \frac{\vec k}{a}\vec v_k
$$

Now, with these, our **CONTINUITY EQUATION** becomes:

$$
\dot{\delta}_k - \frac{\dot a}{a} \frac{i \vec k \cdot \vec r}{a} \delta_k + i \frac{\vec k \cdot \vec v_k}{a} + \frac{\dot a}{a} \left(\vec r \cdot i \frac{\vec{k}}{a}\right)\delta_k = 0
$$

We get cancellations, and thus:

$$
\boxed{\dot \delta_k + i \frac{\vec k \cdot \vec v_k}{a} = 0}
$$

Our Euler equation is:

$$
\dot{\vec v}_k - \frac{\dot a}{a} i \frac{\vec k \cdot \vec r}{a}\vec v_k + \frac{\dot a}{a}\left(\vec r \cdot \frac{i \vec k}{a}\right)\vec v_k + \frac{\dot a}{a}\vec v_k = -v_s^2 \frac{i \vec k}{a}\delta_k - i\frac{\vec k}{a}\Phi_k
$$

We get cancellations and combinations (with total derivatives), giving the **linearized euler equation**!

$$
\boxed{\frac{\partial}{\partial t} \left(a \vec v_k\right) + i v_s^2 \vec k \delta_k + i \vec k \Phi_k = 0}
$$


And our Poisson equation:

$$
\boxed{\frac{k^2}{a^2} \Phi_k = - 4\pi G \rho_0 \delta_k}
$$

And we now combine our three boxed equations in the most efficient way possible for an equation for $\delta$. How do we do that?

1\. We begin by getting rid of $\vec v$. We do this by multiplying our **first** equation by $a^2$. Doing so, this becomes:

$$
a^2 \dot{\delta}_k + i \vec k \cdot \left(a \vec v_k\right) = 0
$$
2\. And we now take $\partial_t$, and use the second equation to replace the first term. This gives, using the second equation above:

$$
a^2 \ddot{\delta}_k + 2a \dot{a} \dot{\delta}_k + i \vec k \cdot (-i v_s^2 \vec k \delta_k - i \vec k \Phi_k) = 0
$$



3\. Divide by $a^2$:

$$
\ddot{\delta}_k + 2 \frac{\dot{a}}{a}\dot{\delta}_k + \frac{v_s^2 k^2}{a^2} \delta_k - \underbrace{4\pi G \rho_0 \delta_k}_\text{using Poisson from above} = 0
$$

And now we have one equation!

$$
\boxed{\ddot{\delta}_k + 2\frac{\dot a}{a} \dot{\delta}_k + \frac{v_s^2}{a^2}\left(k^2 - k_J^2\right)\delta_k = 0}
$$

where 

$$
\boxed{k_J^2 \equiv \frac{4\pi G \rho_0 a^2}{v_s^2}}
$$

Note that this is the **co-moving Jeans wavenumber**, and since $\vec r = a \vec x$, the $a$ cancels out in the physical Jeans wavenumber. The key difference in the above equation is the $\dot{a}/a$ term, by the way, which makes sense for our intuition. Let's look at some regimes.



#### Examine k < k_J regime:

In this case, we have:

$$
\ddot{\delta}_k + 2\frac{\dot a}{a} \dot{\delta}_k - 4\pi G \rho_0 \delta_k = 0
$$

In order to go further, we need to specify our Universe. The simplest case is a flat Universe (Einstein-de Sitter) model. In this case, $\Omega_{m} = 1$ (non-relativistic matter, no curvature, no Cosmological Constant, etc). Recall (or derive), and remember that $a \propto t^{2/3}$ for EdS Universe:

$$
4\pi G \rho  = \frac32 H^2(t) = \frac{\dot{a}^2}{a^2} = \frac{2}{3t^2}
$$

And lastly, our equation for $\ddot{\delta}$ is:

$$
\ddot{\delta}_k + \frac{4}{3t} \dot{\delta}_k - \frac{2}{3t^2} \delta_k = 0
$$

Our Ansatz is: $\delta_k \propto t^{\alpha}$. This makes our expression:

$$
\alpha(\alpha-1) + \frac43 \alpha - \frac23 = 0 \rightarrow \alpha^2 + \frac{\alpha}{3} = \frac23
$$

$$
(\alpha -\frac23)(\alpha+1) = 0  \rightarrow \boxed{\alpha = \frac23 , -1}
$$

What did we find here? **We found that** $\delta \propto t^{2/3} \propto a$ or $\delta \propto t^{-1}$. These represents the growing and decaying mode respectively. We can compare these with the static Universe, in which $\delta$ is exponential $\propto e^{\pm \omega t}$, and not a power law. The thing that slows the exponential growth is the drag term due to the expansion of the Universe.

**The expansion slows to a power-law form, from an exponential form in the static case.** All these different modes, by the way, decouple and have the same behavior. Density perturbations grow like the scale factor in the flat Universe case.


**Take a look into the dark matter power spectrum, by the way!** We derived the time-growth of the power spectrum! The power spectrum of dark matter grows with $a^2$. 


Note that we only solved these expressions for the pertubration growth, but we can do the same with the $\vec v$ and $\Phi$. 



## Gravitational Instability of a Rotating (Self-Gravitating) Disk

Consider a uniformly rotating sheet of zero thickness with constant angular velocity $\vec \Omega = \Omega \hat{z}$. We assume a constant surface density $\Sigma_0$. We also assume the sheet is in the $(x,y)$ plane at $z=0$. Usually, it's easier to go into the moving frame. Thus, we go into the rotating frame. 

In the frame that rotates with the unperturbed sheet, consider small perturbations in the $(x,y)$ plane. 

$$
\Sigma(x,y,t) = \Sigma_0 + \Sigma_1 (x,y,t)
$$

And note that our 3D density, knowing that our disk is razor thin, is:

$$
\rho = \Sigma \cdot \delta(z)
$$

We have a fluid moving in the disk with velocity:

$$
\vec v(x,y,t) = \vec v_0 + \vec v_1(x,y,t)
$$

In the rotating frame, $\vec v_0 = 0$, and thus:

$$
\vec v(x,y,t) = \vec v_1(x,y,t)
$$
As a consequence of going into the rotating frame, we will have to deal with fictitious forces later. 

Our pressure is:

$$
P(x,y,t) = P_0 + P_1(x,y,t)
$$
Note that, because we are in 2D, our sound speed is defined a bit differently, such that:

$$
v_s^2 = \frac{\partial P}{\partial \Sigma} = \frac{P_1}{\Sigma_1}
$$

Which is a statement saying that pressure acts only in the plane, and not upward or donward. 

And potential:

$$
\Phi(x,y,t) = \Phi_0 + \Phi_1(x,y,t)
$$


**The fluid equations take the following form.**


```{admonition} Continuity in 2javascript

\frac{\partial \Sigma}{\partial t} + \vec \nabla (\Sigma \vec v)= 0 \rightarrow \text{ Perturbed } \rightarrow \boxed{\frac{\partial \Sigma_1}{\partial t} + \Sigma_0 \vec \nabla \cdot \vec v = 0 }

```

```{admonition} Euler Equation


$$
\frac{\partial \vec v}{\partial t} + (\vec v \cdot \vec \nabla) \vec v = -\frac{1}{\Sigma} \vec \nabla P - \vec \Phi \underbrace{- 2\vec \Omega \times \vec v}_\text{Coriolis} + \underbrace{\Omega^2 \left(x\hat{x} + y\hat{y}\right)}_\text{centrifugal force}
$$

Note that this is where we have to pay the price of going to the rotating frame. Those extra terms might look ugly, but they're not all that bad.

We can write down our perturbed pieces:

$$
\boxed{\frac{\partial \vec v_1}{\partial t} = -\frac{v_s^2}{\Sigma_0} \vec \nabla \Sigma_1 - \vec \nabla \Phi_1 - 2\vec \Omega \times \vec v}
$$

```

```{admonition} Poisson

$$
\nabla^2 \Phi = 4\pi G \Sigma \delta(z)
$$

Perturbing this, we find:

$$
\boxed{\nabla^2 \Phi_1 = 4\pi G \Sigma_1 \delta(z)}
$$


```

Note that the boxed equations are the perturbed equations. This is pretty similar to what we had before, but we have a nasty coriolis term which prevents our usual tricks.