# Viscous Flows

## Viscous Stress Tensor and the Viscous Force

Viscosity is a measure of of fluid "friction" – the resistance a material has to being deformed by sheer stress. Shear stresses can be pointing in every direction, but has a spatial gradient. 

Water is wet. What does this mean? It really means that it's viscous at the molecular level! Without viscosity, you would come out of a swimming pool totally dry. Can we "derive" viscosity from first principles? Kinda of.…

### Heuristic: Miscroscopic/Molecular Origin of Viscosity

Viscosity arises from _diffusive_ momentum transfer due to particle scattering. Consider a shear flow $\vec v = v_y(x)\hat{y}$. Note in the diagram below, the axes are labelled wrong. Rotate by 90 degrees. Consider the forces on  a volume element $A \cdot \Delta x$. 

Consider sitting at $x$, which is one of the flow arrows in the diagram below. At location $x$, particles receive momentum transfer from those at $x - \frac{l}{2}$ and $x+\frac{l}{2}$ where $l$ is the mean free path, and adjacent fluid elements are spearated by $\Delta x \gg l$. 


```{image} ../figures/fig19.png
:alt: fig19
:width: 600px
:align: center
```

Now consider particles at $x+ \frac{l}{2}$, which have $\hat{y}$-momentum of: $mv_y\left(l+\frac{l}{2}\right)$. 

Now consider particles at $x- \frac{l}{2}$, which have $\hat{y}$-momentum of: $mv_y\left(l-\frac{l}{2}\right)$. 

1\. Thus the net $\hat{y}$-momentum transfer per particle across the boundary $x$ is:

$$
p_y(x) \approx m \frac{\partial v_y}{\partial x} \cdot l
$$
2\. We want to consider the flux, now. We need the number of particles per unit time passing through $x$. This is simpy:

$$
n \cdot v_{th} \cdot A \text{ where } v_{th} \sim \sqrt{\frac{kT}{m}}
$$

is the typical thermal speed of these particles.

Together, these two points give the net momentum transfer through $\hat{x}$:

$$
\dot{p}_y(x) \approx m \frac{\partial v_y}{\partial x} l \cdot n v_{th} A
$$
Remind yourself what the time derivative of momentum is – it's a force! We can now consider the net force between adjacent fluid elements. 

**The viscous force is the net force on element $A \cdot \Delta x$ by surrounding fluids.** Thus,

$$
F_y = \dot{P}_y (x+\Delta x) - \dot{p}_y(x) \approx \frac{\partial \dot{p}}{\partial x} \Delta x 
$$

We can use our expression for $p_y(x)$ from above. This gives:

$$
F_y \approx A \cdot \Delta x \frac{\partial}{\partial x} \left(m \cdot n \cdot l \cdot v_{th} \cdot \frac{\partial v_y}{\partial x}\right)
$$
And now the viscous force per unit volume can be written as:

$$
\frac{F_y}{A \cdot \Delta x} \approx \frac{\partial}{\partial x} \left(\rho \cdot \nu \frac{\partial v_y}{\partial x}\right)
$$
where $\rho = mn$ is the mass density, and $\nu = l v_{th}$ is the **kinematic viscosity** and has units of $\text{cm}^{2} \text{ s}^{-1}$. Sometimes, we combine terms even more:

$$
\eta \equiv \rho \nu \equiv m\cdot n \cdot l \cdot v_{th}
$$

where $\eta$ is called the **dynamic viscosity**. In this re-arrangment, we can write:

$$
\frac{F_y}{A \cdot \Delta x} \approx \frac{\partial }{\partial x}\left(\eta \frac{\partial v_y}{\partial x}\right)
$$

And lastly, we can group together the parentheses, giving:

$$
\boxed{\frac{F_y}{A \cdot \Delta x} \approx \frac{\partial }{\partial x}\left(\sigma_{yx}\right)}
$$
where

$$
\boxed{\sigma_{yx} \equiv \eta \frac{\partial v_y}{\partial x} }
$$

is called the **viscous/shear stress "tensor."**

This derivation is almost correct, but not quite the whole story. 

### Constructing the Viscous Stress Tensor

Let's try to contrusct the tensor from the start, with the condition that it is linear in the velocity gradient. This means:

$$
\frac{\partial v_i}{\partial x_j} = \partial_j v_i \text{ for } i =1,2,3
$$

The most general form is thus:

$$
\sigma_{ij} \equiv \eta \left(\partial_j v_i  + \alpha \partial_i v_j + \beta \delta_{ij} \underbrace{\partial_k v^k}_\text{divergence term}\right)
$$

We can now apply some conditions to constraing $\alpha$ and $\beta$. 

1\. We know that $\sigma_{ij} = 0$ for a uniform, solid-body under rotation, i.e., no shearing/viscous force. For uniform rotation, we have:

$$
\vec v = \Omega R \hat{\phi}
$$

where $\phi$ is the polar-coordinate direction in the $x,y$ plane. Recall as well that: $\hat{r} = \cos \phi \hat{x} + \sin \phi \hat{y}$ and $\hat{\phi} = -\sin \phi \hat{x} + \cos \phi \hat{y}$. Let's use this:

$$
\vec v = \Omega R \left(-\sin \phi \hat{x} + \cos \phi \hat{y}\right) = -\Omega \left(y\hat{x} - x\hat{y}\right)
$$
Let's now look at the component $\sigma_{xy}$:

$$
\sigma_{xy} \propto \partial_y v_x + \alpha \partial_x v_y \propto -1+\alpha = 0 \rightarrow \alpha = 1
$$
2\. Isotropically expanding fluid (Hubble Flow). In this case, we ALSO know that $\sigma_{ij} = 0$. The flow is radially outward, and thus we have no shear. In this case, we have $\vec v \propto \vec r \propto x \hat x + y \hat y + z \hat z$. We can immediately see that the ineresting case has $\sigma_{xx}$ or the like. All other terms vanish. We have:

$$
\sigma_{xx} \propto 1 + \alpha + 3\beta = 0 (\text{ no shear })
$$
And thus:

$$
\beta = -\frac{1 + \alpha}{3} \rightarrow \beta = -\frac{2}{3}
$$

3\. We are finished! Let's collect our results. We just showed that:


$$
\sigma_{ij} = \eta \left(\partial_j v_i + \partial_i v_j - \frac{2}{3} \delta_{ij} \partial_k v^k\right)
$$
Note that this is a **traceless** tensor of rank 2.


## Navier-Stokes Equation and Reynold's Number

Recall the stress tensor:

$$
T_{ij} = \underbrace{P \delta_{ij} }_\text{ thermal pressure } + \underbrace{\rho v_i v_j}_\text{ram pressure} \underbrace{- \sigma_{ij}}_\text{viscous term}
$$


Remember that momentum conservation (Euler's Equation) tells us that:

$$
\frac{\partial}{\partial t} (\rho v_i) = - \partial_j T_{ij} - \rho \partial_i \Phi
$$
With our new viscosity term (per unit volume), we get a new piece to this equation:

$$
\frac{\partial}{\partial t} (\rho v_i) = - \partial_j T_{ij} - \rho \partial_i \Phi + \partial_j \sigma_{ij}
$$

And using our form for $\sigma_{ij}$:

$$
\frac{\partial }{\partial t}\left(\rho v_i\right) = \eta \left(\nabla^2 v_i + \partial_i \left(\vec \nabla \cdot \vec v\right) - \frac23 \partial_{i} (\vec \nabla \cdot \vec v )\right) = \eta \left(\nabla^2 v_i + \frac13 \partial_i \left(\vec\nabla\cdot \vec v\right)\right)
$$


**Our momentum equation in our original form thus becomes the Navier-Stokes Equation:**

```{admonition} Navier Stokes Equation

$$
\frac{\partial \vec v}{\partial t} + (\vec v \cdot \vec \nabla) \vec v = -\frac{1}{\rho}\vec \nabla P - \vec \nabla \Phi \underbrace{+ \underbrace{\nu}_\text{kinematic viscos.}\left(\nabla^2 \vec v + \frac13 \vec \nabla (\vec \nabla \cdot \vec v)\right)}_\text{viscous force per unit mass}
$$

```

```{admonition} Some comments....

1\. For incompressible fluids, $\vec \nabla (\vec \nabla \cdot \vec v) = 0$. 

2\. Viscosity shows up in the momentum equation as a diffusion term, e.g.:

$$
\frac{\partial \vec v}{\partial t} = \nu \nabla^2 \vec v
$$

This should remind us of the drunkard's walk, which makes sense since this comes from molecular momentum transfer. The typical form of the solution for 1D diffusion is:

$$
\vec v(x,t) \propto \frac{1}{\sqrt{\nu t}}e^{-\frac{x^2}{4\nu t}}
$$

3\. You can add a traceful term into $\sigma_{ij}$ which manifests as a **bulk-viscosity**. We do this by:

$$
\sigma_{ij} \rightarrow \sigma_{ij} + \gamma \delta_{ij} \partial_k v^k
$$

for some phenomenonological forces. 

4\. Kinematic Viscosity $\nu$ (diffusion coefficient with units of length squared over time) for some materials at room temperature:

* Water has $\nu = 0.01 \text{ cm}^2 \text{ s}^{-1}$
* Air has $\nu = 0.01 \text{ cm}^2 \text{ s}^{-1}$
* Oil has $\nu = 1\text{ cm}^2 \text{ s}^{-1}$
* Syrup has $\nu \sim 1000\text{ cm}^2 \text{ s}^{-1}$



```

