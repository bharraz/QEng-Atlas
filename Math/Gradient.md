#math

**∇f points in the direction of steepest ascent, with magnitude equal to the slope in that direction** — it's the vector that turns "how does f change if I step in direction n̂" into a dot product, $df = \nabla f \cdot d\mathbf{l}$.

# Reference

Cartesian:
$$
\nabla f = \frac{\partial f}{\partial x}\hat{x} + \frac{\partial f}{\partial y}\hat{y} + \frac{\partial f}{\partial z}\hat{z}
$$

In cylindrical and spherical the components pick up metric factors ($1/s$, $1/r$, $1/r\sin\theta$) — see the full table in [[Curvilinear Coordinates]]. Don't guess these mid-derivation.

**The workhorse radial results** (memorize):
$$
\nabla r = \hat{r}, \qquad \nabla\frac{1}{r} = -\frac{\hat{r}}{r^2}, \qquad \nabla f(r) = f'(r)\,\hat{r}
$$

**Physics:** $\mathbf{E} = -\nabla V$ — fields point downhill in potential, perpendicular to equipotentials. Same structure for any conservative force $\mathbf{F} = -\nabla U$: dipole traps, pseudopotentials, gravity. Gradient vanishing = equilibrium; its second derivatives (Hessian) decide stability.

**Gotcha:** $\nabla f$ is perpendicular to level surfaces of $f$. If your computed field isn't normal to the equipotentials you drew, one of them is wrong.

> [!question]- Why is $\nabla f$ perpendicular to surfaces of constant $f$?
> Along any direction $d\mathbf{l}$ lying in the level surface, $df = \nabla f \cdot d\mathbf{l} = 0$ by definition of the surface — so $\nabla f$ has no component along it. All the change is normal to the surface.

# Connections

- [[Curvilinear Coordinates]] — the lookup table for ∇ in cylindrical and spherical
- [[Electrostatic Potential and Poisson Equation]] — E = −∇V is where this gets used daily
- [[Divergence]] — ∇· of the gradient gives the Laplacian
- [[Taylor Expansion]] — the gradient is the first-order term of f in several variables

---
Source: Griffiths, *Introduction to Electrodynamics*, §1.2
