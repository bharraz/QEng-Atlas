#quantum

**The quantum state drawn as a phase-space distribution — real, normalized, with correct marginals — except it can go negative, and that negativity is precisely the part no classical probability picture can reproduce.** It is the closest quantum mechanics comes to answering "where is the state in phase space."

# Reference

$$
W(x,p) = \frac{1}{\pi\hbar}\int_{-\infty}^{\infty} dy\; \langle x+y|\rho|x-y\rangle\, e^{-2ipy/\hbar}
$$

- $W$ — Wigner quasi-probability density (1/(J·s), one over action): normalized so $\int W\,dx\,dp = 1$
- $x, p$ — phase-space coordinates
- $y$ — the *separation* between bra and ket positions: the off-diagonal coordinate of $\rho$, which is where coherence lives

The structure is a Fourier transform in that separation: $W$ converts the density matrix's off-diagonal extent into momentum information, so a state's coherences (large $y$ support) become its momentum-space structure, and a decohered state's $\rho$ collapsing toward the diagonal shows up as $W$ smearing in $p$.

**Picture:** a phase-space map of the state that reads as a probability density along every line you project onto, but can dip negative in places, the mark of non-classical interference.

**Marginals are true probability distributions:** $\int W\,dp = \langle x|\rho|x\rangle$ and $\int W\,dx = \langle p|\rho|p\rangle$ — project the quasi-distribution onto any quadrature axis and you get the genuinely measurable distribution (rotated quadratures included: that's how homodyne tomography inverts back to $W$).

**Common states, at a glance:**

| State | $W$ |
|---|---|
| Vacuum / coherent | Gaussian (vacuum width), centered at $0$ / $\alpha$ |
| Squeezed | elliptical Gaussian, same area |
| Thermal | fat centered Gaussian, positive |
| Fock $n\geq1$ | rings with **negative** annuli; central value $W(0,0) = \frac{(-1)^n}{\pi\hbar}$ |
| Cat state | two Gaussian peaks + interference fringes oscillating negative between them |

**Negativity = nonclassicality certificate:** Hudson's theorem — a pure state has $W \geq 0$ iff it is Gaussian. Negative regions mean no classical ensemble of phase-space points reproduces the statistics; loss and decoherence wash negativity out fast (fringes decay at a rate scaling with the separation of the two Gaussians — why large cat states decohere fastest).

Related distributions with different orderings: $P$ (normal order; highly singular for nonclassical states) and $Q = \langle\alpha|\rho|\alpha\rangle/\pi$ (antinormal; always positive but smeared). Wigner (symmetric order) is the compromise between them.

> [!question]- $W$ has correct marginals along every quadrature — so in what sense is it *not* a probability distribution?
> Joint interpretation fails: $W(x,p) < 0$ in regions, so you can't read it as "probability of being at $(x,p)$" — $x$ and $p$ don't commute, so no joint distribution exists. Only its one-dimensional projections are physical probabilities.

# Connections

- [[Coherent States]] — the Gaussian states, whose Wigner functions are positive
- [[Bosonic Codes]] — cat and GKP code words, and negativity as the verification signature
- [[Quantum State Tomography (Atlas)]] — homodyne marginals → inverse Radon → $W$
- [[Squeezed States]] — quadrature variances read directly off the ellipse
- [[Fock States]] — negativity in its purest form
- [[Homodyne Detection]] — the measurement whose statistics are $W$'s marginals
- [[Controlling Bosonic Modes]] — measuring the Wigner function by displaced parity

---
Source: Gerry & Knight, *Introductory Quantum Optics*, §3.8
