#circuits #electronics

**Modulate the quantity you want, multiply the detector output by the reference, and low-pass the product: the signal at $f_{\text{ref}}$ lands at DC while everything else averages away.** The result is a bandpass filter of arbitrarily high $Q$ centred exactly on your modulation — unbuildable as an analog filter, trivial once the band of interest has been moved to DC. It is the standard escape from the $1/f$ region, and the single most effective small-signal technique in the lab.

# Reference

Signal $V_s(t) = A\cos(\omega_r t + \phi)$ against reference $\cos\omega_r t$:

$$V_s \cdot V_{\text{ref}} = \frac{A}{2}\Big[\cos\phi + \cos(2\omega_r t + \phi)\Big] \;\xrightarrow{\text{LPF}}\; \frac{A}{2}\cos\phi.$$

- $A$ — signal amplitude at the modulation frequency (V)
- $\phi$ — its phase relative to the reference (rad)

The $2\omega_r$ term is removed by the output filter. **Dual-phase** instruments multiply by both $\cos\omega_r t$ and $\sin\omega_r t$:

$$X = \tfrac{A}{2}\cos\phi, \qquad Y = \tfrac{A}{2}\sin\phi, \qquad R = \sqrt{X^2+Y^2}, \qquad \theta = \arctan(Y/X).$$

**Picture:** only the component that keeps step with the reference survives a long average; everything else drifts in and out of phase with it and cancels.

$R$ is immune to phase drift; $X$ and $Y$ retain the phase information, which is itself the measurement in impedance and dispersive work.

**Why the noise rejection is so large.** The detection band is the *output filter's* bandwidth, translated up to sit centred on $f_{\text{ref}}$. A 1 s time constant gives roughly 0.25 Hz of bandwidth around, say, 10 kHz — an effective $Q$ of $4\times10^4$, and 100 s gives $4\times10^6$. No analog bandpass filter is stable at such $Q$; the lock-in achieves it because the filtering happens at DC where a simple RC is enough. What survives is only noise within that narrow band *and* correlated with the reference phase.

## Instrument anatomy

- **Input stage** — single-ended or differential (differential rejects common-mode pickup, [[Common-Mode and Differential-Mode Signals]]); AC or DC coupled; voltage or current (transimpedance) input. Choose input impedance deliberately: 1 MΩ for high-impedance sources, 50 Ω for terminated RF ([[Time Constants and Reactance Rules of Thumb]]).
- **Preamplifier** — this sets the noise floor, and the choice is the usual $e_n$–$i_n$ versus source impedance match ([[Amplifier Noise]]). A lock-in cannot improve a bad front end; it only narrows the bandwidth around it.
- **Reference channel** — a PLL locks the internal oscillator to an external reference (TTL from a chopper, or a sine), or the instrument's own oscillator drives the modulator. The PLL's own bandwidth matters if the reference jitters ([[Phase-Locked Loops]]).
- **Demodulator** — an analog multiplier in older instruments, a digital multiply after the ADC in modern DSP lock-ins. The distinction is not cosmetic (see harmonics below).
- **Output filter** — time constant $\tau$ and filter order, which together set the detection bandwidth.

## Settings that decide the measurement

**Time constant and filter order.** Equivalent noise bandwidth for the common roll-offs:

| Roll-off | ENBW | Settling to 99% |
|---|---|---|
| 6 dB/oct (1-pole) | $1/4\tau$ | ~5$\tau$ |
| 12 dB/oct | $1/8\tau$ | ~7$\tau$ |
| 18 dB/oct | $3/32\tau$ | ~9$\tau$ |
| 24 dB/oct | $5/64\tau$ | ~10$\tau$ |

Higher order gives more rejection per unit $\tau$ but longer settling — and *always* wait several $\tau$ per point when scanning, or the scan smears the lineshape and shifts peaks ([[Window Functions and Apodization]] — the output filter is a window in time).

**Sensitivity and dynamic reserve.** Sensitivity sets the full-scale input range; dynamic reserve is the ratio (in dB) of the largest tolerable interferer to full scale. High reserve tolerates a large interferer but costs output stability and adds noise; low reserve is cleaner but overloads. **Hidden overload: an overload occurs at the input, where you cannot see it, while the output still shows a plausible number.** Watch the overload indicator, and if a reading changes when you change sensitivity without changing the signal, you were overloaded.

**Choosing $f_{\text{mod}}$** — four constraints at once: above the $1/f$ corner of detector plus preamp (kHz and up, [[Flicker Noise]]); inside the detector's bandwidth; away from line frequency and *all* its harmonics; away from mechanical and acoustic resonances. Use non-round values (1.234 kHz rather than 1 kHz) so that no harmonic of anything in the room lands on it.

**Square versus sine reference.** A square-wave demodulator also responds to odd harmonics of $f_{\text{mod}}$ with weight $1/n$ — interference at $3f$ enters at $-10$ dB, at $5f$ at $-14$ dB. Digital lock-ins multiplying by a true sine do not have this path. If a signal appears that should not, check whether something sits at an odd harmonic.

**Harmonic detection** — deliberately demodulating at $2f$ or $3f$ measures derivatives of the response with respect to whatever you modulated, which is the basis of derivative spectroscopy and of many line-locking schemes.

## Practical failure modes

- **Reference feedthrough**: the modulation couples directly into the signal path (capacitively, through ground, or optically), producing an offset indistinguishable from signal. Test by blocking the physical signal while leaving the modulation running — the output should go to zero.
- **$R$ is biased at low SNR**: $\sqrt{X^2+Y^2}$ rectifies noise, so $\langle R\rangle > 0$ even with no signal (Rice distribution). At low SNR set the phase and use $X$, which is unbiased.
- **Phase drift** with temperature, cable length, or modulation frequency — re-autophase after changing any of them.
- **Ground loops** between the chopper/modulator and the detector, which inject line-synchronous interference right where you are most sensitive ([[Ground Loops]]).

## Related instruments and techniques

The mathematics is a [[Mixers|mixer]] plus a low-pass filter, run at audio frequencies with high dynamic range. [[Pound-Drever-Hall Locking]] is the same modulate-and-demodulate move at RF on an optical carrier. [[Noise Spectroscopy and Filter Functions|Dynamical decoupling]] is its quantum analogue — a pulse train is a reference waveform and the filter function is the detection band. Boxcar averaging is the time-domain counterpart for pulsed rather than continuous signals. In all four, the principle is the same: correlate against a known reference so that everything uncorrelated averages down as $1/\sqrt{T}$ ([[SNR and Averaging]]).

> [!question]- Chopping a beam at 1 kHz makes nW visible on a photodiode that shows nothing at DC — same detector, same light. Where did the sensitivity come from?
> Two effects, and it is worth separating them. First, the measurement moved out of the $1/f$ region: at DC the signal sits under detector and amplifier flicker noise plus thermal drift, while at 1 kHz the floor is white and orders of magnitude lower. Second, the detection bandwidth collapsed: a 1 s time constant admits ~0.25 Hz rather than the DC-to-whatever of an unfiltered measurement, and noise power scales with bandwidth. Neither effect requires a better detector — only that the signal be *modulated*, which is what makes it distinguishable from everything that is not.

# Connections

- [[Mixers]] — the multiplication core, RF edition
- [[Flicker Noise]] — the $1/f$ region this technique avoids rather than averages down
- [[Amplifier Noise]] — the front end that sets the floor the lock-in narrows around
- [[SNR and Averaging]] — the ENBW arithmetic and when longer averaging stops paying
- [[Bandwidth]] — ENBW versus 3-dB bandwidth, and the $\sqrt{B}$ scaling
- [[Pound-Drever-Hall Locking]] — the same move at optical frequencies
- [[Noise Spectroscopy and Filter Functions]] — the qubit implementation of correlated detection
- [[Phase-Locked Loops]] — how the reference channel tracks an external source

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §8.14; Stanford Research Systems, "About Lock-In Amplifiers" (AN3)
