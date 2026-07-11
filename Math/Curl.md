#math

**∇×F is circulation per unit area — how much the field swirls around a point** — shrink a loop around the point; the curl component along the loop's normal is (line integral around it)/(area), sign by right-hand rule (fingers along circulation, thumb gives the curl direction).

# Reference

$$
\nabla\times\mathbf{F} =
\begin{vmatrix}
\hat{x} & \hat{y} & \hat{z} \\
\partial_x & \partial_y & \partial_z \\
F_x & F_y & F_z
\end{vmatrix}
$$
The determinant mnemonic is Cartesian-only — in cylindrical/spherical use the table in [[Curvilinear Coordinates]].

**The two structural identities** (both follow from mixed partials commuting):
$$
\nabla\times(\nabla f) = 0, \qquad \nabla\cdot(\nabla\times\mathbf{A}) = 0
$$
These are why potentials exist: curl-free fields come from a scalar potential ($\mathbf{E} = -\nabla V$ in statics), divergence-free fields from a vector potential ($\mathbf{B} = \nabla\times\mathbf{A}$, always).

**Physics:** the two curl Maxwell equations are the dynamic ones — Faraday $\nabla\times\mathbf{E} = -\partial_t\mathbf{B}$ and Ampère–Maxwell $\nabla\times\mathbf{B} = \mu_0\mathbf{J} + \mu_0\varepsilon_0\partial_t\mathbf{E}$. Curl of curl gives the wave equation via $\nabla\times(\nabla\times\mathbf{F}) = \nabla(\nabla\cdot\mathbf{F}) - \nabla^2\mathbf{F}$.

**Gotcha:** a field can swirl visibly yet have zero curl ($\hat{\phi}/s$ — irrotational vortex, curl is a delta at the axis), and a straight shear flow can have nonzero curl. Curl is local rotation (drop a paddle wheel), not global geometry.

> [!question]- Why does ∇·B = 0 guarantee a vector potential A exists with B = ∇×A?
> Divergence-free is exactly the integrability condition: div of any curl vanishes identically, and (on nice domains) the converse holds — every divergence-free field is a curl. Same logic pairs curl-free with gradients.

# Connections

- [[Stokes and Divergence Theorems]] — Stokes turns circulation integrals into curl fluxes
- [[Vector Potential]] — B = ∇×A exists because div curl = 0
- [[Maxwell's Equations]] — both dynamic equations are curl equations
- [[Curvilinear Coordinates]] — ∇× components in cylindrical and spherical
- [[Helmholtz Decomposition]] — curl specifies the divergence-free part of a field

---
Source: Griffiths, *Introduction to Electrodynamics*, §1.2.5 & §1.3.4
