#quantum #AMO

**Red-detune the light: a moving atom Doppler-shifts the opposing beam toward resonance, scatters preferentially against its motion, and feels a friction force.** Cooling stops where friction balances the random recoil kicks — the Doppler limit.

# Reference

Scattering force from one beam (saturation $s_0$, detuning $\delta$, velocity $v$):

$$F = \hbar k\,\frac{\Gamma}{2}\,\frac{s_0}{1 + s_0 + \left(2(\delta - kv)/\Gamma\right)^2}$$

For red detuning ($\delta < 0$), expanding around $v = 0$ gives $F \approx -\alpha v$ — pure damping. (A trapped ion needs only one beam with projection on all trap axes; the trap provides the restoring force and the ion samples both velocity signs.)

**Doppler limit** — friction vs. recoil-kick diffusion balance, optimized at $\delta = -\Gamma/2$, low $s_0$:

$$T_D = \frac{\hbar\Gamma}{2k_B}$$

Numbers: Ca⁺ (397 nm, $\Gamma/2\pi = 21.6$ MHz): $T_D \approx 0.5$ mK. Yb⁺ (369 nm): $\approx 0.47$ mK. Rb (D2): 146 μK; Na: 240 μK. In a $\omega/2\pi = 1$ MHz trap, 0.5 mK means $\bar{n} = k_B T/\hbar\omega \approx 10$ — cold enough to be in the Lamb–Dicke regime and to start sideband cooling, nowhere near the ground state.

**Practical layer:** detuning shallower than $-\Gamma/2$ cools weakly; blue detuning *heats* explosively (the sign flip is the classic "lost my lock" failure mode). High $s_0$ power-broadens and raises the limit: $T \propto \Gamma\sqrt{1+s_0}$-ish. Ions with low-lying $D$ states need repumpers or cooling stalls on the dark-state timescale.

> [!question]- Why can't Doppler cooling reach the motional ground state, and what breaks the limit?
> The same scattering that damps also kicks: each photon absorption/emission is a random $\hbar k$ recoil, a diffusion floor giving $T_D = \hbar\Gamma/2k_B \gg \hbar\omega/k_B$ for typical traps. Beating it requires decoupling cooling rate from linewidth — resolved sidebands ($\omega \gg \Gamma_{\mathrm{eff}}$) or dark-state methods (EIT cooling).

# Connections

- [[Optical Bloch Equations]] — the scattering-rate formula the force is built from
- [[Resolved Sideband Cooling]] — the second stage that takes over at $\bar{n} \sim 10$ and reaches $\bar{n} \approx 0$
- [[Saturated Absorption Spectroscopy]] — the same Doppler physics used as a lock reference instead of a brake
- [[Lamb-Dicke Regime]] — Doppler cooling's endpoint conveniently lands you inside it

---
Source: Foot, *Atomic Physics*, Ch. 9
