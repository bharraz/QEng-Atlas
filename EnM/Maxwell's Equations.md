#EnM

**Charges source diverging E, there are no magnetic charges, changing B curls E, and currents plus changing E curl B — all of electromagnetism is these four statements plus the Lorentz force.** The displacement current term $\partial_t \mathbf{E}$ is what lets the fields sustain each other and radiate.

# Reference

| Law | Differential | Integral | Says |
|---|---|---|---|
| Gauss | $\nabla\cdot\mathbf{E}=\rho/\varepsilon_0$ | $\oint\mathbf{E}\cdot d\mathbf{a}=Q_{enc}/\varepsilon_0$ | charge makes E diverge |
| No monopoles | $\nabla\cdot\mathbf{B}=0$ | $\oint\mathbf{B}\cdot d\mathbf{a}=0$ | B lines never end |
| Faraday | $\nabla\times\mathbf{E}=-\partial_t\mathbf{B}$ | $\oint\mathbf{E}\cdot d\boldsymbol{\ell}=-\dot{\Phi}_B$ | changing B drives E loops |
| Ampère–Maxwell | $\nabla\times\mathbf{B}=\mu_0\mathbf{J}+\mu_0\varepsilon_0\partial_t\mathbf{E}$ | $\oint\mathbf{B}\cdot d\boldsymbol{\ell}=\mu_0 I_{enc}+\mu_0\varepsilon_0\dot{\Phi}_E$ | current & changing E drive B loops |

**In matter:** define $\mathbf{D}=\varepsilon_0\mathbf{E}+\mathbf{P}$ and $\mathbf{H}=\mathbf{B}/\mu_0-\mathbf{M}$; then only *free* charge and current appear:
$$\nabla\cdot\mathbf{D}=\rho_f, \qquad \nabla\times\mathbf{H}=\mathbf{J}_f+\partial_t\mathbf{D}$$
Linear media: $\mathbf{D}=\varepsilon\mathbf{E}$, $\mathbf{B}=\mu\mathbf{H}$ — bound charge bookkeeping hidden in $\varepsilon,\mu$.

**Waves follow immediately:** curl of Faraday + Ampère in vacuum gives $\nabla^2\mathbf{E}=\mu_0\varepsilon_0\,\partial_t^2\mathbf{E}$, i.e. light at $c=1/\sqrt{\mu_0\varepsilon_0}$ — see [[Electromagnetic Wave Equation]].

> [!question]- What breaks if you delete the displacement current term?
> Ampère's law becomes inconsistent with charge conservation ($\nabla\cdot\mathbf{J}=-\partial_t\rho$ fails for a charging capacitor), and the curl-curl derivation yields no wave equation — no light. Maxwell's term is the whole ballgame.

# Connections

- [[Electromagnetic Wave Equation]] — the two curl equations chained together in vacuum
- [[Electromagnetic Boundary Conditions]] — the integral forms applied to interface pillboxes and loops
- [[Stokes and Divergence Theorems]] — the machinery converting differential ↔ integral forms
- [[Faraday Induction]] — Faraday's law as a circuit/pickup phenomenon
- [[Gauge Freedom]] — the potentials that generate these fields aren't unique

---
Source: Griffiths, *Introduction to Electrodynamics*, Ch. 7.3
