#quantum

**The whole formalism is six rules: states are rays, observables are Hermitian operators, probabilities come from the Born rule, measurement collapses, closed systems evolve unitarily, composites tensor together.** Everything else in this vault's quantum section is consequences.

# Reference

| Postulate | Statement |
|---|---|
| State | Physical state ↔ ray $\|\psi\rangle$ in Hilbert space (norm 1, global phase unphysical) |
| Observable | Measurable quantity ↔ Hermitian $A = \sum_a a\,\|a\rangle\langle a\|$; outcomes are eigenvalues |
| Born rule | $P(a) = \|\langle a\|\psi\rangle\|^2$; expectation $\langle A\rangle = \langle\psi\|A\|\psi\rangle$ |
| Collapse | Outcome $a$ ⇒ state becomes $P_a\|\psi\rangle/\sqrt{P(a)}$ (projector onto the eigenspace) |
| Evolution | $\|\psi(t)\rangle = U(t)\|\psi(0)\rangle$, $U = e^{-iHt/\hbar}$ unitary — deterministic between measurements |
| Composition | Joint system lives in $\mathcal{H}_A \otimes \mathcal{H}_B$; entanglement = states that don't factor |

**The tension worth remembering:** evolution is linear, deterministic, and reversible; measurement is stochastic and irreversible. All interpretation fights live in that seam. Operationally you never need to resolve it — [[Density Matrix]] + [[Projective Measurement and POVMs]] handle every lab situation, including open systems and weak measurements where the naive collapse rule is too blunt.

> [!question]- Which postulate forbids deterministically distinguishing non-orthogonal states?
> The Born rule: if $\langle\phi|\psi\rangle \neq 0$, any measurement that sometimes fires on $|\phi\rangle$ also fires on $|\psi\rangle$ with nonzero probability. Unitarity then makes this permanent — no evolution changes overlaps.

# Connections

- [[Dirac Notation]] — the language the postulates are written in
- [[Projective Measurement and POVMs]] — the measurement postulate generalized to the form you actually use
- [[Density Matrix]] — states when you're ignorant or entangled; postulates restated with $\rho$
- [[Schrodinger Equation]] — the evolution postulate in differential form
- [[Tensor Product]] — the composition postulate's machinery

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, Ch. 1
