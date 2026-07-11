#math

**The one differential equation the lab runs on: drive a lossy oscillator and, after transients die, it responds at the drive frequency with a Lorentzian amplitude and a phase that walks through 90° at resonance.** Cavity field, RLC tank, atomic dipole, ion motion — same equation, different labels.

# Reference

$$
\ddot{x} + \gamma\dot{x} + \omega_0^2 x = \frac{F_0}{m}\cos\omega t
$$

**Steady state** $x(t) = A\cos(\omega t - \phi)$:
$$
A(\omega) = \frac{F_0/m}{\sqrt{(\omega_0^2-\omega^2)^2 + \gamma^2\omega^2}}, \qquad \tan\phi = \frac{\gamma\omega}{\omega_0^2 - \omega^2}
$$

**Phase is the fingerprint:** $\phi\to 0$ far below resonance (spring-like, in phase), $\phi = 90°$ exactly at $\omega_0$ regardless of $\gamma$, $\phi\to 180°$ far above (mass-like, inverted). At resonance the velocity is in phase with the force — maximum power transfer.

**Near resonance** ($|\Delta| = |\omega-\omega_0| \ll \omega_0$) it collapses to the universal Lorentzian:
$$
A(\Delta) \propto \frac{1}{\sqrt{\Delta^2 + (\gamma/2)^2}}, \qquad \text{FWHM (power)} = \gamma
$$

**Transient:** the homogeneous solution rings at $\omega_0' = \sqrt{\omega_0^2 - \gamma^2/4}$ and decays as $e^{-\gamma t/2}$ (amplitude) — so the steady state is "reached" after a few $2/\gamma$. Lock acquisition, cavity buildup, and ringdown measurements all live in this transient.

| Incarnation | $x$ | $\gamma$ | drive |
|---|---|---|---|
| Mechanical / ion in trap | position | friction | applied force / RF tickle |
| Series RLC | charge | $R/L$ | source voltage |
| Cavity field | mode amplitude | $\kappa$ | input laser |
| Atomic dipole (weak drive) | coherence | $\Gamma$ | laser field |

> [!question]- The drive is exactly at $\omega_0$. Why is the response 90° out of phase with the force, independent of damping?
> At $\omega=\omega_0$ the stiffness ($\omega_0^2 x$) and inertia ($\ddot x$) terms cancel exactly, leaving $\gamma\dot x = F/m$: the force balances the *damping*, so it's in phase with velocity — which leads displacement by 90°. This is why error signals built from the phase are steepest right at resonance.

# Connections

- [[Resonance and Q Factor]] — the figure of merit for this equation's response, in all its incarnations
- [[LC Resonators]] — the circuit realization; $\omega_0 = 1/\sqrt{LC}$, $\gamma = R/L$
- [[Optical Bloch Equations]] — the atomic dipole is this oscillator plus saturation
- [[Green's Functions]] — the impulse response $e^{-\gamma t/2}\sin\omega_0' t$ is this system's Green's function

---
Source: Taylor, *Classical Mechanics*, Ch. 5 (Oscillations)
