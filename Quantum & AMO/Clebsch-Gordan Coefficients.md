#quantum #AMO

**The change-of-basis numbers between "two separate angular momenta" $|j_1 m_1\rangle|j_2 m_2\rangle$ and "one total" $|J M\rangle$.** You never derive them mid-calculation — you look them up; what you memorize is which ones vanish.

# Reference

$$|J M\rangle = \sum_{m_1, m_2} \langle j_1 m_1; j_2 m_2 | J M\rangle \; |j_1 m_1\rangle |j_2 m_2\rangle$$

$j_1, j_2$ = the two angular momenta being added (dimensionless, in units of $\hbar$ — e.g. electron spin and orbital, or $I$ and $J$ for hyperfine); $m_1, m_2$ = their $z$-projections; $J, M$ = total and its projection; the coefficient $\langle j_1 m_1; j_2 m_2 | J M\rangle$ is a real dimensionless overlap between the two bases. Both bases span the same $(2j_1{+}1)(2j_2{+}1)$-dimensional space, so this is a rotation of basis, not new physics — the coefficients are fixed by geometry alone and are the *same numbers* for spins, orbitals, or photon polarizations.

**Vanishing rules** (the useful part):
- $M = m_1 + m_2$ — z-components just add
- triangle: $|j_1 - j_2| \le J \le j_1 + j_2$

All coefficients are real in the Condon–Shortley convention. Stretched states are trivial: $|J{=}j_1{+}j_2,\, M{=}J\rangle = |j_1 j_1\rangle|j_2 j_2\rangle$; ladder down for the rest. Tables: PDG, or `sympy.physics.quantum.cg`.

**Wigner–Eckart is why you care:** for a spherical tensor operator $T^k_q$ (dipole: $k=1$),

$$\langle \alpha' j' m' | T^k_q | \alpha j m \rangle = \langle j m; k q | j' m' \rangle \, \langle \alpha' j' \| T^k \| \alpha j \rangle$$

— geometry (a Clebsch–Gordan coefficient) factors out of physics (one reduced matrix element per line). So relative strengths between Zeeman/hyperfine sublevels of the same transition are *pure* CG ratios: one number from experiment or theory, the whole $m_F$-resolved intensity pattern for free. This is what sits under branching-ratio bookkeeping and optical-pumping calculations.

> [!question]- A transition's $\sigma^+$ and $\pi$ Rabi frequencies between specific $m_F$ levels differ. What did you need to compute, and what did you look up?
> Compute nothing but one reduced matrix element $\langle F' \| d \| F \rangle$ (or take it from the measured lifetime); the $m_F, q$ dependence is entirely the Clebsch–Gordan factor $\langle F m_F; 1 q | F' m_F'\rangle$ — Wigner–Eckart.

# Connections

- [[Angular Momentum in QM]] — the addition rules these coefficients implement
- [[Selection Rules]] — $\Delta m$, $\Delta F$ rules are exactly the CG vanishing conditions
- [[Optical Pumping]] — its rate equations are Clebsch–Gordan bookkeeping in action

---
Source: Sakurai, *Modern Quantum Mechanics*, §3.8 (Wigner–Eckart §3.11)
