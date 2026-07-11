#quantum #AMO

**A linear drive $\cos\omega t$ splits into two circular components; only the one co-rotating with the transition matters, so drop the counter-rotating term oscillating at $\sim 2\omega$.** Averages to nothing over the timescales you care about — valid when $\Omega \ll \omega$.

# Reference

Two-level system driven at $\omega$ near $\omega_0$, in the frame rotating at $\omega$:
$$
H = \frac{\hbar\Omega}{2}\left(\sigma_+ e^{-i\omega t} + \sigma_+ e^{+i\omega t} + \text{h.c.}\right)\cdot(\text{frame}) \;\longrightarrow\; H_{\text{RWA}} = -\frac{\hbar\Delta}{2}\sigma_z + \frac{\hbar\Omega}{2}\sigma_x
$$
The kept term $\sigma_+ e^{-i\omega t}$ becomes static; the dropped one becomes $\sigma_+ e^{+i2\omega t}$ — a perturbation flipping the spin *against* energy conservation, oscillating too fast to accumulate.

**Validity:** $\Omega, |\Delta| \ll \omega_0$. Fine for optical transitions ($\Omega/\omega \sim 10^{-8}$); check it for RF/microwave hyperfine drives at strong power, strong-coupling circuit QED, and ultrafast pulses.

**The leading correction — Bloch-Siegert shift:** the counter-rotating term isn't exactly zero, it level-repels in second order and pulls the apparent resonance by
$$
\delta\omega_{BS} \approx \frac{\Omega^2}{4\omega_0}
$$
matters when calibrating qubit frequencies at high Rabi power.

Same move in field quantization: keeping $a\sigma_+ + a^\dagger\sigma_-$ (excitation-number conserving) and dropping $a\sigma_- + a^\dagger\sigma_+$ is what turns the Rabi model into the solvable [[Jaynes-Cummings Model]].

> [!question]- Why exactly does the counter-rotating term contribute so little, and what does it do in second order?
> In the rotating frame it oscillates at $2\omega$: its first-order effect time-averages to zero over any evolution slow compared to $1/2\omega$. In second order it survives as a level shift (like any off-resonant coupling, $\sim\Omega^2/4\omega_0$) — the Bloch-Siegert shift.

# Connections

- [[Interaction Picture]] — where the $e^{\pm i2\omega t}$ factors become visible to drop
- [[Rotating Frame Transformation]] — the frame change performed before the approximation
- [[Jaynes-Cummings Model]] — RWA applied to the quantized field
- [[Complex Numbers and Phasors]] — the classical shadow: keeping one of two counter-rotating phasors
- [[Rabi Oscillations]] — the clean dynamics that emerge once RWA is made

---
Source: Cohen-Tannoudji, Dupont-Roc & Grynberg, *Atom-Photon Interactions*, Ch. II & VI
