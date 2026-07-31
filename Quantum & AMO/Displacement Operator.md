#quantum

**The operator that rigidly translates phase space by $\alpha$ — and because displacements along different directions don't commute, a closed loop of them leaves behind a pure phase equal to twice the enclosed area.** That phase is geometric, state-independent, and is the engine of the Mølmer-Sørensen gate.

# Reference

$$
D(\alpha) = e^{\alpha a^\dagger - \alpha^* a}, \qquad D^\dagger(\alpha)\, a\, D(\alpha) = a + \alpha, \qquad D(\alpha)|0\rangle = |\alpha\rangle
$$

$\alpha$ = complex displacement (dimensionless): its real and imaginary parts are the shifts in the two quadratures, measured in units of the ground-state spread $x_0 = \sqrt{\hbar/2m\omega}$, and $|\alpha|^2 = \bar n$ is the mean quanta added. The exponent is anti-Hermitian ($\alpha a^\dagger - \alpha^* a$), which is what makes $D$ unitary; in position–momentum language it is $e^{i(p_0\hat x - x_0\hat p)/\hbar}$, so momentum generates position shifts and vice versa.

Unitary, $D^\dagger(\alpha) = D(-\alpha)$. Normal-ordered form (from BCH, since $[a, a^\dagger]=1$ is central): $D(\alpha) = e^{-|\alpha|^2/2}\,e^{\alpha a^\dagger}e^{-\alpha^* a}$.

**The composition phase — THE point of this card.** BCH with $[A,B]$ a c-number gives $e^A e^B = e^{A+B}e^{[A,B]/2}$, hence
$$
D(\alpha)\,D(\beta) = e^{i\,\mathrm{Im}(\alpha\beta^*)}\; D(\alpha + \beta)
$$
Displacements add like vectors, but the product picks up a phase = the signed area of the triangle they span (×2). Chain displacements around a **closed loop** in phase space and the operator collapses to pure phase:
$$
D_{\text{loop}} = e^{i\Phi}\,\mathbb{1}, \qquad \Phi = 2 \times (\text{enclosed area in } \alpha\text{-plane})
$$
**Geometric, not dynamical:** $\Phi$ depends only on the loop's area — not on speed, path shape at fixed area, or the motional starting state (thermal, coherent, whatever). A *spin-dependent* force makes $\alpha(t)$ conditional on the qubit state → different loop areas → entangling phase, with the motion disentangled once the loop closes. That is the [[Molmer-Sorensen Gate]], and why it tolerates $\bar n \neq 0$.

Also the generator view: $D = e^{i(p_0\hat x - x_0\hat p)/\hbar}$-type object — momentum displaces position and vice versa; a resonant force pulse on an ion mode literally applies $D(\alpha)$ with $\alpha \propto \int F(t)e^{i\omega t}dt$.

> [!question]- Why is the phase from a closed displacement loop independent of the oscillator's initial state?
> Each composition step's phase $\mathrm{Im}(\alpha\beta^*)$ comes from $[a, a^\dagger] = 1$ — a c-number, not an operator. The accumulated phase multiplies the identity rather than acting on the state, so vacuum, Fock, or hot thermal states all acquire exactly $e^{i2A}$. Geometry in, state out.

# Connections

- [[Baker-Campbell-Hausdorff]] — the identity generating the composition phase
- [[Coherent States]] — $D(\alpha)$ applied to vacuum, by definition
- [[Molmer-Sorensen Gate]] — spin-dependent loops cashing the area phase as entanglement
- [[Squeezed States]] — the other Gaussian unitary; together they generate all Gaussian states
- [[Wigner Function]] — where "rigid translation of phase space" is literal

---
Source: Gerry & Knight, *Introductory Quantum Optics*, §3.2
