#quantum

**Squash the uncertainty circle: noise in one quadrature drops below the vacuum level, at the cost of the conjugate quadrature blowing up to keep $\Delta X_1 \Delta X_2 \geq 1/4$.** Quantum noise isn't a floor — it's a budget you can reallocate.

# Reference

Squeeze operator (quadratic in $a$ — a two-photon/parametric process by construction):
$$
S(\xi) = \exp\!\left[\tfrac{1}{2}\left(\xi^* a^2 - \xi\, a^{\dagger 2}\right)\right], \qquad \xi = r e^{i\theta}
$$

$\xi$ = complex squeezing parameter; $r \geq 0$ = squeeze magnitude (dimensionless — the exponent by which one quadrature's noise shrinks, $e^{-r}$), $\theta$ = squeeze angle (rad), with the squeezed quadrature oriented at $\theta/2$ — halved because $S$ is quadratic in $a$, the same factor-2 that makes a $2\omega$ parametric drive act at $\omega$; $a, a^\dagger$ = mode annihilation/creation operators (dimensionless). $r$ accumulates as (parametric gain rate) × (interaction time), and noise falls exponentially in it: 8.7 dB per unit $r$.

Acting on vacuum, with quadratures $X_1 = (a + a^\dagger)/2$, $X_2 = (a - a^\dagger)/2i$ (vacuum: $\Delta X_i = 1/2$):
$$
\Delta X_1 = \tfrac{1}{2}e^{-r}, \qquad \Delta X_2 = \tfrac{1}{2}e^{+r} \quad (\theta = 0)
$$
Still minimum-uncertainty — an ellipse of the same area, orientation set by $\theta/2$. Squeezing quoted in dB: $10\log_{10}(e^{-2r})$; $r = 1.15$ ≈ 10 dB. Squeezed vacuum contains photons ($\bar n = \sinh^2 r$), only *even* number states — it's $a \to a\cosh r - a^\dagger e^{i\theta}\sinh r$ (Bogoliubov transformation).

**Where it comes from:** any Hamiltonian $\propto a^2 + a^{\dagger 2}$ — parametric down-conversion, four-wave mixing, modulating a trap frequency at $2\omega$ (parametric drive on an ion's motion squeezes the same way).

**Why you care:** homodyne detection locked to the squeezed quadrature beats the shot-noise limit — LIGO runs squeezed light routinely; spin squeezing is the same idea for atomic clocks beating projection noise. **Gotcha: loss is lethal** — mixing in vacuum through efficiency $\eta$ degrades toward $\Delta X^2 \to \eta\,\Delta X_{sq}^2 + (1-\eta)/4$; 3 dB of loss caps you near 3 dB of usable squeezing no matter what the source made.

> [!question]- Squeezing doesn't violate the uncertainty principle — so where does the "free" sensitivity come from?
> The product $\Delta X_1\Delta X_2$ is unchanged; you've rotated the noise into the quadrature you don't measure. It only pays if your measurement genuinely uses one quadrature (homodyne at fixed phase) — measure both and the advantage cancels.

# Connections

- [[Coherent States]] — the round blob this deforms; displaced squeezed states combine both
- [[Vacuum Fluctuations]] — the noise floor being redistributed
- [[Homodyne Detection]] — the quadrature-selective measurement that cashes in
- [[Wigner Function]] — squeezed states: elliptical Gaussians, still positive
- [[Displacement Operator]] — composes with $S(\xi)$ to build the full Gaussian-state family

---
Source: Gerry & Knight, *Introductory Quantum Optics*, Ch. 7
