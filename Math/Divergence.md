#math

**∇·F is outflow per unit volume — flux density** — shrink a closed surface around a point; divergence is (flux out)/(volume enclosed) in the limit. Positive = source, negative = sink, zero = whatever flows in flows out.

# Reference

Cartesian:
$$
\nabla\cdot\mathbf{F} = \frac{\partial F_x}{\partial x} + \frac{\partial F_y}{\partial y} + \frac{\partial F_z}{\partial z}
$$
Cylindrical/spherical forms have $\frac{1}{r^2}\partial_r(r^2 F_r)$-type structure — table in [[Curvilinear Coordinates]].

**Divergence theorem** (the integral–differential bridge):
$$
\oint_S \mathbf{F}\cdot d\mathbf{a} = \int_V (\nabla\cdot\mathbf{F})\, dV
$$

**The point-charge trap:** the Coulomb field looks divergence-free everywhere you can differentiate it, but the flux through any sphere is $4\pi$ — all the divergence hides at the origin:
$$
\nabla\cdot\left(\frac{\hat{r}}{r^2}\right) = 4\pi\,\delta^3(\mathbf{r})
$$
This one identity is Gauss's law: $\nabla\cdot\mathbf{E} = \rho/\varepsilon_0$ for a point charge, done.

**∇·B = 0** — no magnetic charges, field lines never end, which is why $\mathbf{B} = \nabla\times\mathbf{A}$ exists. **Incompressible flow** means $\nabla\cdot\mathbf{v}=0$: same math, volume conservation instead of charge.

> [!question]- The field $\hat{r}/r^2$ has $\nabla\cdot\mathbf{F}=0$ by direct differentiation for $r>0$, yet $\oint\mathbf{F}\cdot d\mathbf{a}=4\pi$ over any enclosing sphere. Reconcile.
> The divergence theorem still holds — the divergence is a delta function at the origin, where the naive derivative formula doesn't apply. Integrating $4\pi\delta^3(\mathbf{r})$ over the volume gives exactly $4\pi$.

# Connections

- [[Stokes and Divergence Theorems]] — the integral form and orientation conventions
- [[Maxwell's Equations]] — the two divergence equations (Gauss, no monopoles)
- [[Dirac Delta]] — where the point-charge divergence actually lives
- [[Curvilinear Coordinates]] — ∇· in cylindrical and spherical
- [[Helmholtz Decomposition]] — divergence specifies the curl-free part of a field

---
Source: Griffiths, *Introduction to Electrodynamics*, §1.3 & §1.5.3
