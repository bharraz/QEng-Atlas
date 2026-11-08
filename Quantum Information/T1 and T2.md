#quantum-info

**$T_1$ is how long the qubit holds its energy; $T_2$ is how long it holds its phase.** On the Bloch sphere: $T_1$ shrinks $z$ toward equilibrium, $T_2$ shrinks the $xy$ plane — and losing energy necessarily scrambles phase, so $T_2 \le 2T_1$.

# Reference

From the Lindblad rates (decay $\sqrt{\Gamma}\sigma_-$, pure dephasing $\sqrt{\gamma_\varphi/2}\,\sigma_z$):

$$
\frac{1}{T_1} = \Gamma, \qquad \frac{1}{T_2} = \frac{1}{2T_1} + \gamma_\varphi \;\;\Rightarrow\;\; T_2 \le 2T_1
$$

- $\Gamma$ — energy relaxation rate (s⁻¹): how fast excited-state population decays to the ground state
- $\gamma_\varphi$ — pure dephasing rate (s⁻¹): randomizes phase without moving population

Rates add because independent decoherence channels add in rate, never in time. The $\tfrac12$ is the field-vs-power factor again: $T_1$ describes populations ($\propto$ amplitude²) while $T_2$ describes the coherence amplitude itself, so the same decay costs the coherence half as much. A decay-limited qubit ($\gamma_\varphi = 0$) therefore has $T_2 = 2T_1$, the factor 2 coming from that population-vs-amplitude difference.

**Picture:** the Bloch vector's two ways to fade: $T_1$ lets it fall toward the pole, $T_2$ lets the arrows of different runs fan out around the equator until their average vanishes.

**$T_2^*$ vs $T_2$**: shot-to-shot and ensemble inhomogeneity (B-field drift, laser detuning wander) adds quasi-static dephasing → free-induction decays in $T_2^* \le T_2$. It's reversible: a $\pi$ pulse refocuses the static part, so echo recovers the "true" $T_2$.

**What measures what:**

| Experiment | Sequence | Yields |
|---|---|---|
| Inversion recovery | $\pi$ — wait $t$ — measure | $T_1$ |
| Ramsey | $\pi/2$ — $T$ — $\pi/2$ | $T_2^*$ (fringe contrast decay) |
| Hahn echo | $\pi/2$ — $\tau$ — $\pi$ — $\tau$ — $\pi/2$ | $T_2$ |

**Decay shape carries spectral information:** exponential ⇒ white dephasing noise, Gaussian ⇒ slow/$1/f$-dominated (and then quoting a single "$T_2$" number is already a lie). Echo $\gg$ Ramsey time is the standard fingerprint of low-frequency noise.

> [!question]- Ramsey gives 100 μs, echo gives 2 ms, inversion recovery gives 10 s. What's the noise budget?
> $T_1$ is irrelevant ($1/2T_1$ negligible). Dephasing dominates and is almost entirely quasi-static — refocusable drift (B-field, laser frequency), not fast noise. Fix the slow environment or add dynamical decoupling; improving $T_1$ gains nothing.

# Connections

- [[Lindblad Master Equation]] — where $\Gamma$ and $\gamma_\varphi$ live as jump rates
- [[Spin Echo and Dynamical Decoupling]] — why $T_2^* \ne T_2$ and how to close the gap
- [[Ramsey Interferometry]] — the $T_2^*$ measurement itself
- [[Bloch Sphere]] — the shrink-$z$ vs shrink-$xy$ picture

---
Source: Nielsen & Chuang, Ch. 8.3.5–8.3.6 (amplitude and phase damping)
