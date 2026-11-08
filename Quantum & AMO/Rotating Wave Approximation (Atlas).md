#quantum #AMO

**A two-level system with transition frequency $\omega_0$ is driven by a field oscillating as $\cos\omega t$, with $\omega$ near $\omega_0$; the linear drive splits into two circular components rotating in opposite senses, and only the one co-rotating with the transition stays in step with it.** The counter-rotating term oscillates at $\sim 2\omega$ relative to the system, averages to nothing over the timescales you care about, and is dropped — valid when $\Omega \ll \omega$.

# Reference

Lab-frame Hamiltonian of the driven two-level system:

$$
H = \frac{\hbar\omega_0}{2}\sigma_z + \hbar\Omega\cos(\omega t)\,(\sigma_+ + \sigma_-)
$$

With $\cos\omega t = \tfrac12(e^{i\omega t} + e^{-i\omega t})$, the drive sorts into two pairs:

$$
\hbar\Omega\cos(\omega t)\,(\sigma_+ + \sigma_-) = \underbrace{\tfrac{\hbar\Omega}{2}\left(\sigma_+ e^{-i\omega t} + \sigma_- e^{+i\omega t}\right)}_{\text{co-rotating}} + \underbrace{\tfrac{\hbar\Omega}{2}\left(\sigma_+ e^{+i\omega t} + \sigma_- e^{-i\omega t}\right)}_{\text{counter-rotating}}
$$

- $\omega_0$ — transition frequency (rad/s)
- $\omega$ — drive frequency (rad/s); $\Delta = \omega - \omega_0$ is the detuning
- $\Omega$ — Rabi frequency (rad/s), the drive strength
- $\sigma_\pm$ — raise and lower the two-level system: rotate as $e^{\pm i\omega_0 t}$ under free evolution

In the frame rotating at $\omega$ ([[Rotating Frame Transformation]]), $\sigma_\pm \to \sigma_\pm e^{\pm i\omega t}$. The kept term $\sigma_+ e^{-i\omega t}$ becomes static; the dropped one becomes $\sigma_+ e^{+i2\omega t}$ — a perturbation flipping the spin *against* energy conservation, oscillating too fast to accumulate. Dropping it leaves

$$
H_{\text{RWA}} = -\frac{\hbar\Delta}{2}\sigma_z + \frac{\hbar\Omega}{2}\sigma_x
$$

**Picture:** a merry-go-round seen from a co-rotating horse: the field component rotating with you looks stationary and acts steadily, while the counter-rotating one whirls past at twice the speed and averages out.

**Validity:** $\Omega, |\Delta| \ll \omega_0$. Fine for optical transitions ($\Omega/\omega \sim 10^{-8}$); check it for RF/microwave hyperfine drives at strong power, strong-coupling circuit QED, and ultrafast pulses.

**The leading correction — Bloch-Siegert shift:** the counter-rotating term isn't exactly zero; it level-repels in second order and pulls the apparent resonance by
$$
\delta\omega_{BS} \approx \frac{\Omega^2}{4\omega_0}
$$
which matters when calibrating qubit frequencies at high Rabi power.

The same approximation in field quantization: keeping $a\sigma_+ + a^\dagger\sigma_-$ (excitation-number conserving) and dropping $a\sigma_- + a^\dagger\sigma_+$ is what turns the Rabi model into the solvable [[Jaynes-Cummings Model (Atlas)]].

> [!question]- Why exactly does the counter-rotating term contribute so little, and what does it do in second order?
> In the rotating frame it oscillates at $2\omega$: its first-order effect time-averages to zero over any evolution slow compared to $1/2\omega$. In second order it survives as a level shift (like any off-resonant coupling, $\sim\Omega^2/4\omega_0$) — the Bloch-Siegert shift.

# Connections

- [[Interaction Picture]] — where the $e^{\pm i2\omega t}$ factors become visible to drop
- [[Rotating Frame Transformation]] — the frame change performed before the approximation
- [[Jaynes-Cummings Model (Atlas)]] — RWA applied to the quantized field
- [[Complex Numbers and Phasors]] — the classical shadow: keeping one of two counter-rotating phasors
- [[Rabi Oscillations]] — the clean dynamics that emerge once RWA is made

---
Source: Cohen-Tannoudji, Dupont-Roc & Grynberg, *Atom-Photon Interactions*, Ch. II & VI
