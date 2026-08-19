#quantum-info #AMO

**Every quantum sensor runs the same three steps — prepare a superposition, let the signal accumulate phase, read the phase out — so the whole subject is about what limits the phase you can resolve.**

# Reference

$$\text{initialize} \;\to\; \underbrace{\phi = \gamma \int_0^\tau V(t)\,dt}_{\text{accumulate}} \;\to\; \text{read out}$$

$\gamma$ = the coupling converting the quantity you want into a precession rate. Everything a platform does is a choice of $\gamma$, of how long $\tau$ can be, and of how well the phase can be read.

**The sensitivity formula, in the form that transfers between platforms:**
$$\eta \;\sim\; \frac{1}{\gamma\, C \sqrt{N\,\tau}} \qquad \left[\text{signal}/\sqrt{\text{Hz}}\right]$$

with $C$ the readout contrast, $N$ the number of probes, $\tau$ the interrogation time per shot. Three things follow, and they set every design decision:

- **Contrast enters linearly, coherence only as $\sqrt\tau$.** Improving readout fidelity is worth more than an equal fractional improvement in $T_2$. This is why single-shot readout schemes matter so much ([[Spin-Dependent Fluorescence and ODMR]]).
- **$\sqrt\tau$, not $\tau$** — phase accumulates linearly in $\tau$ but fewer shots fit in a fixed averaging window, so the gain is square-root.
- **$\tau$ is capped by coherence, and which coherence depends on the signal.**

## DC vs AC: the sequence is a filter

| Signal | Sequence | Limited by | Because |
|---|---|---|---|
| Static | **Ramsey** | $T_2^*$ | quasi-static environment noise accumulates identically to the signal |
| Oscillating at $f$ | **echo / dynamical decoupling** | $T_2 \gg T_2^*$ | flipping the probe cancels slow noise but *not* a signal synchronized with the flips |

A decoupling sequence is a **band-pass filter** on environmental noise, and its passband is set by the pulse spacing. So the same sequence that protects coherence also selects a signal frequency — protection and lock-in detection are one operation ([[Noise Spectroscopy and Filter Functions]], [[Spin Echo and Dynamical Decoupling]]).

**Run it backwards and it is a spectrometer.** Sweep the pulse spacing, watch the coherence decay rate, and you map $S(\omega)$ of the environment. Sensing and noise characterization are the same measurement read in opposite directions.

**Dynamic range trades against sensitivity.** Phase wraps at $2\pi$, so a longer $\tau$ resolves smaller signals but aliases larger ones. Fixes: adaptive or phase-estimation protocols that start with short $\tau$ and refine, or run several $\tau$ in parallel and reconstruct.

## The quantum limits

| Limit | Scaling of $\Delta\phi$ | Requires |
|---|---|---|
| **Standard quantum limit** | $1/\sqrt N$ | $N$ independent probes — just counting statistics |
| **Heisenberg limit** | $1/N$ | entanglement (GHZ) or squeezing |

The SQL is not a quantum mystery: it is the [[Central Limit Theorem]] applied to $N$ independent binary outcomes. The Heisenberg limit is the genuinely quantum statement, and the general machinery behind both is Fisher information — the [[Fisher Information and the Cramér-Rao Bound|Cramér–Rao bound]] gives $\Delta\phi \ge 1/\sqrt{F}$, with the quantum Fisher information setting the best any measurement could do.

**The honest caveat on entanglement.** A GHZ state accumulates phase $N$ times faster, but also decoheres $N$ times faster, so under realistic dephasing the net gain often evaporates. **Spin squeezing** is the practical middle ground — a modest, robust improvement rather than the full $1/N$ ([[Standard Quantum Limit and Spin Squeezing]]).

## What the platforms trade

| Sensor | $\gamma$ couples to | Distinguishing feature |
|---|---|---|
| **NV centre** | magnetic field, via $\gamma_e$ | nanometres from the sample, room temperature; ensembles trade spatial resolution for $\sqrt N$ ([[NV Centers (atlas)]]) |
| **Trapped-ion clock** | frequency, via the transition | best absolute accuracy; long $\tau$ from excellent isolation |
| **Atom interferometer** | acceleration, rotation, $g$ | free-fall path enclosing area; $\gamma$ scales with the enclosed area |
| **Optomechanics / LIGO** | displacement | squeezed light beats the shot-noise limit directly ([[Cavity Optomechanics]], [[Squeezed States]]) |
| **Atomic vapour magnetometer** | magnetic field | competitive with SQUIDs without cryogenics |

Reading across: **the same formula with a different $\gamma$**. What differs is not the physics of estimation but which coupling is available and how long the probe survives.

**Other quantities from the same probe.** Any term in the sensor's Hamiltonian that shifts with an external quantity becomes a sensing channel: for NV, $dD/dT$ gives thermometry and the strain term $E$ gives electrometry, with no change to the sequence — only to what you calibrate against.

> [!question]- Doubling $T_2$ improves your sensitivity by $\sqrt2$. Doubling readout contrast improves it by 2. Why the asymmetry?
> $\eta \propto 1/(C\sqrt\tau)$. Coherence buys interrogation time, and longer shots mean proportionally fewer of them in a fixed window, so the gain is square-root. Contrast is per-shot information, with no compensating loss — it enters linearly. Hence effort spent on readout fidelity usually beats equal effort on coherence.

# Connections

- [[Fisher Information and the Cramér-Rao Bound]] — the general bound behind SQL and Heisenberg scaling
- [[Standard Quantum Limit and Spin Squeezing]] — entanglement-enhanced sensing and its fragility
- [[Noise Spectroscopy and Filter Functions]] — the sequence as a filter, and as a spectrometer
- [[Spin Echo and Dynamical Decoupling]] — extending $\tau$ from $T_2^*$ to $T_2$
- [[Ramsey Interferometry]] — the DC phase-accumulation sequence
- [[NV Centers (atlas)]] / [[Spin-Dependent Fluorescence and ODMR]] — the worked solid-state case
- [[Squeezed States]] — beating shot noise in the optical version
- [[Central Limit Theorem]] — why the SQL is $1/\sqrt N$
- [[SNR and Averaging]] — the classical averaging this sits on top of

---
Source: Degen, Reinhard & Cappellaro, "Quantum sensing," *Rev. Mod. Phys.* 89, 035002 (2017); Giovannetti, Lloyd & Maccone, *Nat. Photonics* 5, 222 (2011)
