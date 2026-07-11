 #AMO

**Split the spin onto the equator, let it accumulate phase freely for time $T$, then close the interferometer: the fringe reads out frequency to $\sim 1/T$.** Precision comes from the *dark* time — the drive is only there to open and close.

# Reference

Sequence: $\tfrac{\pi}{2}$ — free evolution $T$ — $\tfrac{\pi}{2}$. A detuning $\delta$ (or any qubit-frequency offset) winds phase $\phi = \delta T$ on the equator; the second pulse converts phase to population:

$$P_e = \frac{1}{2}\left[1 + C\cos(\delta T + \varphi)\right]$$

with fringe period $2\pi/T$ in $\delta$ and contrast $C$ decaying on the coherence time ($T_2^*$ for a bare Ramsey). Scanning the second pulse's phase $\varphi$ instead of $\delta$ gives the same fringe without retuning — the standard calibration move.

**Why it beats Rabi spectroscopy:** during $T$ the drive is off — no power broadening, no drive-induced light shifts, no sensitivity to pulse-amplitude error at the fringe's steepest point. Linewidth $\sim 1/T$ is set by *your patience*, not the drive. Frequency sensitivity per shot: $\delta f \sim 1/(2\pi T \cdot C)$, degraded by projection noise as $1/\sqrt{N}$ over $N$ shots — clocks are exactly this, maximized $T$ plus statistics.

**Practical readings:** fringe contrast vs $T$ *is* your $T_2^*$ measurement; fringe center drift is your qubit-frequency (field, light-shift) drift; contrast loss without frequency shift points at dephasing, not miscalibration.

> [!question]- Why is Ramsey more precise than just driving a long weak Rabi pulse of the same total duration?
> Both give $\sim 1/T$ linewidth, but the Rabi line's center is pulled by drive light shifts and its shape entangled with amplitude noise. Ramsey accumulates phase with the drive off — the fringe center depends only on the free-evolution frequency, and pulse-area errors reduce contrast, not the center. Systematics, not statistics, are the win.

# Connections

- [[Rabi Oscillations]] — supplies the $\pi/2$ pulses; Ramsey is two of them and patience
- [[Spin Echo and Dynamical Decoupling]] — insert a $\pi$ pulse to cancel the slow-noise part and push toward $T_2$
- [[T1 and T2]] — Ramsey decay defines $T_2^*$; echo comparison separates the contributions
- [[Binomial Errors in State Detection]] — the projection-noise floor on reading the fringe

---
Source: Foot, *Atomic Physics*, §7.4
