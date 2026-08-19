#EnM

**Seen from far away, any charge blob looks like a point charge, plus a dipole correction, plus a quadrupole correction — an expansion in (source size/distance).** Each order falls off one power of $r$ faster, so only the lowest nonvanishing moment matters at long range.

# Reference

$$
V(\mathbf{r}) = \frac{1}{4\pi\varepsilon_0}\left[\frac{Q}{r} + \frac{\mathbf{p}\cdot\hat{r}}{r^2} + \frac{1}{2r^3}\sum_{ij}Q_{ij}\hat{r}_i\hat{r}_j + \cdots\right]
$$

where $Q=\int\rho\,d^3r$ (monopole), $\mathbf{p}=\int\mathbf{r}'\rho\,d^3r'$ (dipole), $Q_{ij}=\int(3r'_ir'_j - r'^2\delta_{ij})\rho\,d^3r'$ (quadrupole).

**Scalings:** $V\sim 1/r,\ 1/r^2,\ 1/r^3$; fields one power steeper. Expansion parameter is $(d/r)$ with $d$ the source size — each higher order is suppressed by another factor of it.

**Spherical harmonics form** (the systematic version):
$$
V = \frac{1}{4\pi\varepsilon_0}\sum_{l,m} \frac{4\pi}{2l+1}\,\frac{q_{lm}}{r^{l+1}}\,Y_{lm}(\theta,\phi), \qquad q_{lm}=\int r'^l\, Y^*_{lm}\,\rho\,d^3r'
$$

**When higher orders matter:** whenever the lower ones vanish by symmetry — a neutral molecule (no monopole) interacts via dipole; a centrosymmetric one via quadrupole. Same logic in radiation: E1-forbidden atomic transitions proceed by E2/M1, slower by $\sim(ka)^2$ — that hierarchy is why clock transitions are narrow ([[Dipole Approximation]]). Caveats: dipole moment is origin-dependent unless $Q=0$; the expansion assumes you're *outside* the charge distribution.

> [!question]- Why does a neutral atom in a trap still feel electrode potentials, and at what order?
> Zero monopole means no force from a uniform field, but the induced dipole $\mathbf{p}=\alpha\mathbf{E}$ gives energy $-\frac{1}{2}\alpha E^2$ — force from field *gradients*. Neutral-atom traps live entirely at this induced-dipole order.

# Connections

- [[Legendre Polynomials and Spherical Harmonics]] — the angular basis the expansion is organized in
- [[Dipole Radiation]] — the radiating counterpart: dipole term dominates emission too
- [[Dipole Approximation]] — same expansion applied to atom–light coupling; E2 transitions are the next term
- [[Taylor Expansion]] — this is just Taylor in $d/r$, organized by angular momentum
- [[Method of Images]] — complementary trick when you're *near* conductors instead of far from sources

---
Source: Griffiths, *Introduction to Electrodynamics*, Ch. 3.4; Jackson Ch. 4 for the $Y_{lm}$ form
