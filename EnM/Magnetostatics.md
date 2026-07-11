#EnM

**Steady currents make static B fields: Biot–Savart integrates the contributions, Ampère's law shortcuts the symmetric cases.** Three formulas — wire, loop, solenoid — cover most of what a lab ever needs.

# Reference

$$
\mathbf{B}(\mathbf{r}) = \frac{\mu_0}{4\pi}\int \frac{I\,d\boldsymbol{\ell}'\times\hat{\imath}}{r^2}
\qquad\text{(Biot–Savart)}, \qquad
\oint \mathbf{B}\cdot d\boldsymbol{\ell} = \mu_0 I_{enc} \qquad\text{(Ampère)}
$$

**The lookup trio:**

| Geometry | Field |
|---|---|
| Infinite straight wire, distance $s$ | $B = \dfrac{\mu_0 I}{2\pi s}$ (circles the wire, RH rule) |
| Loop radius $R$, on axis at $z$ | $B = \dfrac{\mu_0 I R^2}{2(R^2+z^2)^{3/2}}$ — center: $\mu_0 I/2R$ |
| Long solenoid, $n$ turns/length | $B = \mu_0 n I$ inside, ~0 outside |

**Calibration numbers:** 1 A wire at 1 cm → 0.2 G (20 μT). Earth's field ~0.5 G. Helmholtz pair (spacing = R): $B\approx 0.9\,\mu_0 nI/R$ per side... just remember $8\mu_0 NI/\sqrt{125}R$, uniform to 4th order at the center. Rule for atom/ion work: **~1.4 MHz/G Zeeman sensitivity means mG-level field stability needs mA-level current stability and attention to what's steel near the chamber.**

$\nabla\cdot\mathbf{B}=0$ always — no way to terminate field lines, which is why magnetic shielding must *divert* flux (mu-metal) rather than block it, and why [[Vector Potential]] exists.

> [!question]- Why is a solenoid's field independent of its radius, and where did the energy-per-volume go?
> Ampère's law only counts enclosed current per length, $nI$ — radius drops out. But total stored energy $\frac{B^2}{2\mu_0}\times$ volume grows with $R^2$: fatter solenoid, same field, much more stored energy (and inductance $\mu_0 n^2 A \ell$ says exactly that).

# Connections

- [[Zeeman Effect (Atlas)]] — what those gauss actually do to your atomic levels
- [[Vector Potential]] — $\nabla\cdot\mathbf{B}=0$ guarantees $\mathbf{B}=\nabla\times\mathbf{A}$
- [[Faraday Induction]] — what happens when these currents (and fields) vary
- [[Electromagnetic Shielding]] — why low-frequency B is the hard case
- [[Curvilinear Coordinates]] — Ampère-law problems live in cylindrical coordinates

---
Source: Griffiths, *Introduction to Electrodynamics*, Ch. 5
