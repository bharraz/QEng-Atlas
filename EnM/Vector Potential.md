#EnM

**Because $\nabla\cdot\mathbf{B}=0$ everywhere, B must be the curl of something: $\mathbf{B}=\nabla\times\mathbf{A}$.** A starts as a bookkeeping device but ends up more fundamental than B — quantum phases couple to A directly.

# Reference

$$
\mathbf{B}=\nabla\times\mathbf{A}, \qquad \mathbf{E}=-\nabla V - \frac{\partial\mathbf{A}}{\partial t}
$$

In Coulomb gauge ($\nabla\cdot\mathbf{A}=0$) magnetostatics gives $\nabla^2\mathbf{A}=-\mu_0\mathbf{J}$ — a Poisson equation per component, so
$$
\mathbf{A}(\mathbf{r}) = \frac{\mu_0}{4\pi}\int\frac{\mathbf{J}(\mathbf{r}')}{|\mathbf{r}-\mathbf{r}'|}\,d^3r'
$$
— **A is "shaped like the current"** (points along J, falls off like a potential). Useful instant intuition: a solenoid's A circles azimuthally even *outside*, where B = 0.

**Why it's more than bookkeeping:**
- **Aharonov–Bohm:** an electron encircling a solenoid picks up phase $\frac{q}{\hbar}\oint\mathbf{A}\cdot d\boldsymbol{\ell} = q\Phi/\hbar$ despite touching zero B — interference shifts observably. Flux, via A, is physical even where fields vanish.
- **Minimal coupling:** charged-particle QM couples through $\mathbf{p}\to\mathbf{p}-q\mathbf{A}$; the photon field in quantum optics *is* the quantized A ([[Field Quantization of Light]]).
- Only gauge-invariant things ($\mathbf{B}$, loop integrals $\oint\mathbf{A}\cdot d\boldsymbol{\ell}=\Phi$) are measurable — see [[Gauge Freedom]].

> [!question]- B is exactly zero outside an ideal solenoid — so what does an electron interferometer wrapped around it measure, and why?
> A phase difference $q\Phi/\hbar$ between the two arms. The loop integral of A equals the enclosed flux regardless of the local B, and quantum mechanics couples to A. Locality of forces survives; locality of *phases* does not.

# Connections

- [[Gauge Freedom]] — the non-uniqueness $\mathbf{A}\to\mathbf{A}+\nabla\chi$ and how to exploit it
- [[Magnetostatics]] — the current integrals that build A
- [[Helmholtz Decomposition]] — the div-free/curl-free split that motivates potentials
- [[Field Quantization of Light]] — mode-expanding A is how photons enter
- [[Retarded Potentials]] — A's dynamical, causal solution

---
Source: Griffiths, *Introduction to Electrodynamics*, Ch. 5.4 & 10.1
