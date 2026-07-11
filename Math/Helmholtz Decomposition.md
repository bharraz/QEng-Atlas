#math

**Any well-behaved vector field splits uniquely into a curl-free piece plus a divergence-free piece** — specify a field's divergence and curl (plus decay at infinity) and you've specified the field. This is why Maxwell's equations, which are exactly statements about div and curl, determine E and B.

# Reference

$$
\mathbf{F} = -\nabla\varphi + \nabla\times\mathbf{A}
$$
with the potentials built from the field's own sources:
$$
\varphi(\mathbf{r}) = \frac{1}{4\pi}\int \frac{\nabla'\cdot\mathbf{F}(\mathbf{r}')}{|\mathbf{r}-\mathbf{r}'|}\, dV', \qquad
\mathbf{A}(\mathbf{r}) = \frac{1}{4\pi}\int \frac{\nabla'\times\mathbf{F}(\mathbf{r}')}{|\mathbf{r}-\mathbf{r}'|}\, dV'
$$

- $-\nabla\varphi$: **longitudinal** (curl-free) part — carries all the divergence.
- $\nabla\times\mathbf{A}$: **transverse** (divergence-free) part — carries all the curl.
- Uniqueness requires $\mathbf{F} \to 0$ faster than $1/r$ at infinity; on finite domains, boundary terms (a harmonic piece) sneak in.

**In Fourier space it's trivial:** longitudinal = component of $\tilde{\mathbf{F}}(\mathbf{k})$ along $\hat{k}$, transverse = perpendicular. "Longitudinal/transverse" is literal there.

**Physics:** electrostatic $\mathbf{E}$ is pure $-\nabla V$; $\mathbf{B}$ is pure $\nabla\times\mathbf{A}$ (no monopoles); radiation is the transverse part of $\mathbf{E}$ — in Coulomb gauge the split is explicit: instantaneous Coulomb piece + transverse radiation piece. Photons are excitations of the transverse field only; the longitudinal field is bookkeeping for charges.

> [!question]- Why does knowing ∇·F and ∇×F everywhere (with decay at infinity) pin down F completely?
> If two fields share both, their difference has zero div and zero curl — so it's $\nabla h$ with $\nabla^2 h = 0$ everywhere. A harmonic function decaying at infinity is zero (no interior extrema), so the difference vanishes.

# Connections

- [[Vector Potential]] — the divergence-free half is ∇×A by construction
- [[Gauge Freedom]] — the split is gauge-dependent bookkeeping; Coulomb gauge makes it explicit
- [[Maxwell's Equations]] — four div/curl statements = complete field specification via this theorem
- [[Electrostatic Potential and Poisson Equation]] — the curl-free half in the static case

---
Source: Griffiths, *Introduction to Electrodynamics*, Appendix B
