#quantum

**The one problem physics actually solves, so everything gets mapped onto it: equally spaced levels $\hbar\omega(n+\tfrac12)$ built by ladder operators, with a Gaussian ground state that saturates the uncertainty bound.** Trap motion, cavity modes, phonons — all this Hamiltonian.

# Reference

$$
H = \frac{p^2}{2m} + \frac{1}{2}m\omega^2x^2 = \hbar\omega\left(a^\dagger a + \tfrac{1}{2}\right), \qquad E_n = \hbar\omega\left(n + \tfrac{1}{2}\right)
$$

**Ladder solution in one breath:** define $a = \frac{1}{2x_0}x + \frac{i x_0}{\hbar}p$ with $x_0 = \sqrt{\hbar/2m\omega}$; then $[a,a^\dagger] = 1$, $[H,a] = -\hbar\omega a$, so $a$ lowers energy in steps of $\hbar\omega$; positivity of $\langle a^\dagger a\rangle$ terminates the ladder at $a|0\rangle = 0$. Full machinery in [[Ladder Operators]].

**THE conversion formulas** (memorize; convention $x_0 = \sqrt{\hbar/2m\omega}$):
$$
x = x_0\,(a + a^\dagger), \qquad p = i\,\frac{\hbar}{2x_0}\,(a^\dagger - a) = i\sqrt{\frac{m\hbar\omega}{2}}\,(a^\dagger - a)
$$

**Ground state:** Gaussian $\psi_0(x) \propto e^{-x^2/4x_0^2}$ with $\Delta x = x_0$, $\Delta p = \hbar/2x_0$ — minimum uncertainty $\Delta x\,\Delta p = \hbar/2$. Zero-point energy $\hbar\omega/2$ is uncertainty made unavoidable. Excited states: Hermite polynomials × the same Gaussian. (Trapped-ion scale: $^{171}$Yb$^+$ at $\omega/2\pi = 1$ MHz → $x_0 \approx 5$ nm.)

**Equal spacing is what makes it special:** a coherent drive climbs the ladder resonantly at every rung — classical-like motion, coherent states, and clean sideband physics all trace to this. Any anharmonicity breaks it (which is exactly how a transmon isolates a qubit from the ladder).

> [!question]- Why can't the oscillator ground state have zero energy?
> $E = 0$ needs $\langle p^2\rangle = \langle x^2\rangle = 0$ simultaneously — sharp $x$ and $p$, forbidden by $[x,p] = i\hbar$. Minimizing $\frac{\langle p^2\rangle}{2m} + \frac{m\omega^2\langle x^2\rangle}{2}$ subject to $\Delta x\Delta p \geq \hbar/2$ gives exactly $\hbar\omega/2$: zero-point energy is the compromise.

# Connections

- [[Ladder Operators]] — the algebraic engine, in full
- [[Fock States]] — the number eigenstates $|n\rangle$
- [[Hermite Polynomials]] — position-space wavefunctions
- [[Coherent States]] — the classical-motion states of this Hamiltonian
- [[Normal Modes of Ion Chains]] — each mode is one of these

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §2.3
