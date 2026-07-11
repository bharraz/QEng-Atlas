#EnM

**Fields don't know what the source is doing now — they respond to what it did a light-travel-time ago.** Replace $t$ with the retarded time $t_r = t - |\mathbf{r}-\mathbf{r}'|/c$ in the static formulas and (for the potentials) you're exactly right.

# Reference

In Lorenz gauge, the wave equations for the potentials are solved by the static-looking integrals evaluated at retarded time:

$$
V(\mathbf{r},t) = \frac{1}{4\pi\varepsilon_0}\int \frac{\rho(\mathbf{r}', t_r)}{|\mathbf{r}-\mathbf{r}'|}\,d^3r', \qquad
\mathbf{A}(\mathbf{r},t) = \frac{\mu_0}{4\pi}\int \frac{\mathbf{J}(\mathbf{r}', t_r)}{|\mathbf{r}-\mathbf{r}'|}\,d^3r'
$$

$$
t_r = t - \frac{|\mathbf{r}-\mathbf{r}'|}{c}
$$

**Trap:** this works for the *potentials*, not the fields — naively retarding Coulomb's law is wrong (Jefimenko's equations carry extra $\dot\rho$, $\dot{\mathbf{J}}$ terms).

**Why near field ≠ far field:** differentiate the retarded integrand and you get two kinds of terms — ones going as $1/r^2$ (retarded statics, no net energy escape) and ones $\propto \dot{\mathbf{J}}/r$ from the retardation itself. Within $r\ll\lambda/2\pi$ retardation is negligible and the field is **quasi-static** (Coulomb/Biot-Savart, instantaneous for all practical purposes); beyond it the $1/r$ radiation terms dominate. The crossover *is* the [[Near and Far Field]] boundary.

**Practical calibration:** signals in cable propagate at ~2/3 c ≈ 20 cm/ns; free space 30 cm/ns. Retardation across a 30 cm circuit at 10 MHz is 1% of a period — ignorable; at 1 GHz it's 10 periods — the "circuit" is now a distributed system and lumped analysis is dead.

> [!question]- A charge abruptly stops. What does the field configuration look like one second later?
> Inside radius $c\cdot(1\,\mathrm{s})$: the static Coulomb field of the stationary charge. Outside: the field of the still-moving charge, as if nothing happened. The spherical shell stitching them together is a kink of transverse field propagating outward — that kink *is* the radiation.

# Connections

- [[Near and Far Field]] — the quasi-static/radiation split is retardation becoming order-one
- [[Vector Potential]] — the object the retarded integral computes
- [[Gauge Freedom]] — the clean retarded form is a Lorenz-gauge statement
- [[Dipole Radiation]] — expand the retarded integral for a small oscillating source
- [[Transmission Lines]] — what circuits become once retardation across them matters

---
Source: Griffiths, *Introduction to Electrodynamics*, Ch. 10.2; Jackson Ch. 6 for Jefimenko
