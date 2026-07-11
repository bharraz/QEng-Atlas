#quantum #AMO #group-theory

**The Wigner-Eckart theorem factors any matrix element of a spherical tensor operator into a Clebsch-Gordan coefficient (pure geometry, tabulated) times a single reduced matrix element (all the physics, computed once per multiplet pair).** One radial integral then fixes every Zeeman component of a transition — this is why relative line strengths and relative Rabi frequencies are ratios of CG coefficients you never have to calculate.

# Reference

A **spherical tensor operator** $T^k_q$ ($q = -k, \dots, k$) is a set of $2k+1$ operators transforming under rotations like the states $|k, q\rangle$:

$$[J_z, T^k_q] = q\, T^k_q, \qquad [J_\pm, T^k_q] = \sqrt{k(k+1) - q(q\pm1)}\; T^k_{q\pm1}.$$

Rank 0 is a scalar, rank 1 a vector in the spherical basis ($T^1_{\pm1} = \mp(V_x \pm iV_y)/\sqrt{2}$, $T^1_0 = V_z$) — the electric dipole $\hat{d}$ is the canonical rank-1 example; electric quadrupole is rank 2.

**The theorem:**

$$\langle \alpha', j', m' |\, T^k_q\, | \alpha, j, m \rangle = \langle j, m;\, k, q\, |\, j', m' \rangle \, \langle \alpha', j' \| T^k \| \alpha, j \rangle$$

The CG coefficient carries all $m, m', q$ dependence; the **reduced matrix element** $\langle \cdot \| T^k \| \cdot \rangle$ is independent of orientation and contains the radial/dynamical physics. (Convention warning: some texts divide by $\sqrt{2j'+1}$; check before comparing tables.)

**Selection rules fall out for free** — the matrix element vanishes unless the CG coefficient survives:

$$m' = m + q, \qquad |j - k| \leq j' \leq j + k.$$

For dipole ($k=1$): $\Delta m = 0, \pm1$ and $\Delta j = 0, \pm1$ with $j = 0 \not\to j' = 0$. This is [[Selection Rules]] derived in one line, and the $\pi$/$\sigma^\pm$ polarization labels are just $q = 0, \pm 1$.

**Lab payoff — ratios within a multiplet.** For two Zeeman components of the same fine/hyperfine transition, the reduced matrix element cancels:

$$\frac{\Omega_{m_1 \to m_1'}}{\Omega_{m_2 \to m_2'}} = \frac{\langle j, m_1; k, q_1 | j', m_1' \rangle}{\langle j, m_2; k, q_2 | j', m_2' \rangle}.$$

Measure one Rabi frequency, and geometry gives you all the others. Same logic gives branching ratios in spontaneous decay and relative ODMR/spectroscopy line strengths.

**Projection theorem** (rank-1 corollary): within a single $j$-multiplet, every vector operator is proportional to $\mathbf{J}$:

$$\langle j, m' | \mathbf{V} | j, m \rangle = \frac{\langle \mathbf{J} \cdot \mathbf{V} \rangle_j}{j(j+1)\hbar^2}\, \langle j, m' | \mathbf{J} | j, m \rangle.$$

This is the derivation of the Landé $g$-factor: project $\boldsymbol{\mu} = -\mu_B(\mathbf{L} + 2\mathbf{S})/\hbar$ onto $\mathbf{J}$ and read off $g_J = 1 + \frac{j(j+1) + s(s+1) - \ell(\ell+1)}{2j(j+1)}$ (see [[Zeeman Effect (Atlas)]]).

**Group-theoretic content**: the theorem is Schur's lemma applied to the decomposition $j \otimes k = |j-k| \oplus \dots \oplus (j+k)$ — the operator maps the product representation into $j'$, and there is (at most) one invariant way to do that, so a single number suffices (see [[Group Representations]], [[Clebsch-Gordan Coefficients]]).

> [!question]- You've measured the Rabi frequency on one Zeeman component and your next experiment drives a different component of the same transition. Do you need to recalibrate?
> No — divide out the CG coefficient of the measured component and multiply by that of the new one (accounting for laser polarization, which selects $q$). The reduced matrix element — laser intensity, radial wavefunctions — is common to both. Recalibration is only needed if the beam geometry, polarization purity, or intensity changed.

# Connections

- [[Clebsch-Gordan Coefficients]] — the geometric factor the theorem isolates
- [[Selection Rules]] — the vanishing-CG cases, stated as transition rules
- [[Group Representations]] — Schur's lemma is why one number is enough
- [[Zeeman Effect (Atlas)]] — Landé $g$ via the projection theorem
- [[Angular Momentum in QM]] — the multiplet structure everything is expressed in
- [[Rabi Oscillations]] — relative Rabi frequencies across Zeeman components

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, Ch. 3.11; Edmonds, *Angular Momentum in Quantum Mechanics*, Ch. 5
