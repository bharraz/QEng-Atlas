#quantum

**The vacuum displaced to amplitude $\alpha$: eigenstate of the annihilation operator, minimum-uncertainty, and its centroid follows the classical equation of motion exactly.** The closest quantum mechanics gets to "the oscillator is at phase-space point $\alpha$" — and what a laser or a resonantly kicked ion mode actually produces.

# Reference

$$
a|\alpha\rangle = \alpha|\alpha\rangle, \qquad |\alpha\rangle = D(\alpha)|0\rangle = e^{-|\alpha|^2/2}\sum_n \frac{\alpha^n}{\sqrt{n!}}\,|n\rangle
$$

**Number statistics — Poissonian:**
$$
P(n) = e^{-|\alpha|^2}\frac{|\alpha|^{2n}}{n!}, \qquad \bar n = |\alpha|^2, \quad \Delta n = \sqrt{\bar n}
$$
This is the shot-noise reference point: $g^{(2)}(0) = 1$; sub-Poissonian means nonclassical.

**Most classical, by three measures:** (1) minimum uncertainty, $\Delta x\,\Delta p = \hbar/2$ with vacuum-sized noise ($\Delta x = x_0$) — a circular blob in phase space that never spreads; (2) under $H = \hbar\omega a^\dagger a$, $|\alpha\rangle \to |\alpha e^{-i\omega t}\rangle$ — a rigid Gaussian blob orbiting the classical trajectory; (3) a classical drive on the vacuum produces exactly this state. Eigenstate of $a$ (not $a^\dagger$; $a$ isn't Hermitian, so $\alpha \in \mathbb{C}$ and these aren't orthogonal).

**Overcomplete basis:** $\langle\beta|\alpha\rangle = e^{-|\alpha-\beta|^2/2}\,e^{i\,\mathrm{Im}(\beta^*\alpha)} \neq 0$, yet $\frac{1}{\pi}\int d^2\alpha\, |\alpha\rangle\langle\alpha| = \mathbb{1}$ — resolution of identity with a redundant, non-orthogonal family (the basis of P/Q phase-space representations).

Also: losing one photon does nothing — $a|\alpha\rangle \propto |\alpha\rangle$ — which is why coherent states are the pointer states loss decoheres *to*.

> [!question]- Why does photon loss leave a coherent state unchanged while it destroys a Fock state?
> $|\alpha\rangle$ is an eigenstate of $a$: annihilation returns the same state. $|n\rangle$ maps to $|n-1\rangle$ — orthogonal to where it started. Coherent states are the fixed points of the loss channel, which is why open-system dynamics keeps producing them.

# Connections

- [[Displacement Operator]] — the operator that manufactures $|\alpha\rangle$ from vacuum
- [[Poisson Distribution]] — the number statistics
- [[Photon Statistics and g2]] — coherent = $g^{(2)}=1$ benchmark between thermal and Fock
- [[Quantum Harmonic Oscillator]] — the system these are states of
- [[Wigner Function]] — a coherent state is a displaced vacuum Gaussian there

---
Source: Gerry & Knight, *Introductory Quantum Optics*, Ch. 3
