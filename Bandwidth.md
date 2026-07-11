#math #reference

**Bandwidth = how wide a slice of frequency space something occupies — and the one fact under every version of it: a signal of duration $T$ and bandwidth $W$ contains $\approx 2WT$ independent numbers.** Every relation on this page is that counting argument in a different domain's clothes, and every "why is X limited?" question below reduces to "X ran out of degrees of freedom."

# Reference

**Which "bandwidth" do you mean** — the definitions disagree by O(1) factors, and cross-quoting them is a classic silent error (always state which):

| definition          | criterion                       | native habitat                                                                      |
| ------------------- | ------------------------------- | ----------------------------------------------------------------------------------- |
| 3-dB / half-power   | $\|H\|^2$ falls to half peak    | filters, amplifiers, servos                                                         |
| FWHM                | spectral intensity half max     | spectroscopy, laser lines                                                           |
| null-to-null        | first zeros around main lobe    | pulses, RF                                                                          |
| RMS                 | $\sigma_\omega$ of the spectrum | uncertainty relations (the theorem's version)                                       |
| equivalent noise BW | $\int\|H\|^2 df / \|H(f_0)\|^2$ | noise integration — the *only* correct one for converting noise density to variance |
| fractional          | $\Delta\omega/\omega_0$         | "narrowband" ≲ few %, resonator language                                            |

**Time–bandwidth product.** The Fourier uncertainty relation $\Delta t\,\Delta\nu \geq K$ with a shape-dependent constant (FWHM×FWHM): Gaussian 0.441, sech² 0.315, Lorentzian 0.142, rectangular 0.886. Equality = **transform-limited**: no chirp, the shortest pulse that spectrum permits. A measured $\Delta t \Delta\nu$ above the shape's $K$ *quantifies* the chirp. The lab corollary for step responses: **rise time × 3-dB bandwidth ≈ 0.35** (single pole) — a 10 ns edge needs ~35 MHz of analog chain, and any instrument's edge tells you its bandwidth without a datasheet.

**Resonance bandwidth**: $\Delta\omega = \omega_0/Q$ ([[Resonance and Q Factor]]). The time-domain reading matters as much as the frequency one: linewidth = 1/(ring-down time), so a resonator's bandwidth is also its *control* bandwidth — it cannot respond to changes faster than $Q$ cycles (see [[Resonance]]). A cavity, a decaying qubit, and an atomic line are all "an amplitude decaying in time," so they all hand you a Lorentzian whose width is a rate.

**Servo bandwidth** ([[Control Beyond PID]], [[PID Control]]): the frequency where loop gain crosses unity — disturbances below it are suppressed by the (falling) loop gain, disturbances above it pass, and just above it they're *amplified* (the servo bump; the waterbed integral says the suppressed area must go somewhere). "A 100 kHz lock" is a statement about where this crossover sits, capped by delay at $f \lesssim 1/4\tau_{\text{delay}}$.

**Sampling** ([[Sampling and Aliasing]]): $f_s \geq 2B$ — *bandwidth*, not carrier: a 50 MHz-wide signal on a 6 GHz carrier needs ~100 MS/s of IQ sampling, not 12 GS/s. Undersampling on purpose (bandpass sampling) is aliasing used as a free mixer.

**Noise grows with bandwidth — the √B in everything.** White noise of density $S_0$ integrated over bandwidth $B$ gives variance $S_0 B$, amplitude $\propto \sqrt{B}$: narrowing the measurement bandwidth (longer averaging, [[Lock-In Detection|lock-in]] time constants, matched filtering) is the universal SNR lever, at the price of speed — SNR × measurement rate is the conserved commodity ([[SNR and Averaging]]). Thermal noise power is $k_B T B$ ($-174$ dBm/Hz at 300 K); the quantum version appends the zero-point half-photon, $P = \hbar\omega B[\bar n + \tfrac12]$, the floor under phase-insensitive amplification ([[Amplifier Noise]], [[Vacuum Fluctuations]]).

**Channel capacity** (Shannon–Hartley): $C = B\log_2(1 + \mathrm{SNR})$ — linear in bandwidth, logarithmic in power, which is why every communication system since has bought bandwidth instead of watts, and why your data link (or DDS resolution vs update rate trade) behaves the way it does.

**Spatial bandwidth**: NA *is* a spatial-frequency bandwidth ($k_\perp^{\max} = k\,\mathrm{NA}$), the resolution $\delta x \sim \lambda/2\mathrm{NA}$ is its Nyquist statement, and (aperture/λ)·NA counts resolvable spots — $2WT$ with space for time (see [[Numerical Aperture and Spot Size]], [[Diffraction]]). An SLM's pixel count, a grating's resolving power, and an imaging system's field-of-view × resolution trade are all this one budget.

> [!question]- A photodiode amplifier claims 1 MHz bandwidth and 5 pA/√Hz noise. What noise current do you actually compare your signal to — and why is "5 pA" wrong twice?
> Integrate the density over the *equivalent noise bandwidth*, not the 3-dB number: for a single-pole response ENBW $= (\pi/2) \times f_{3\text{dB}} \approx 1.57$ MHz, giving $5\,\text{pA}/\sqrt{\text{Hz}} \times \sqrt{1.57\times10^6} \approx 6.3$ nA rms. "5 pA" errs once by forgetting the √B (units!) and once by using the wrong B — the π/2 is the tax for the filter's soft skirt letting noise through above the corner. Steeper filters shrink ENBW toward the 3-dB value; this is also why lock-in time-constant settings quote an ENBW.

# Connections

- [[Fourier Transform]] — the uncertainty relation this page instantiates everywhere
- [[Resonance and Q Factor]] / [[Resonance]] — $\omega_0/Q$, and sharp-in-frequency = slow-in-time
- [[Laser Linewidth]] — FWHM bandwidth of an emission line, same Lorentzian
- [[Power Spectral Density]] / [[PSD Estimation]] — the density that bandwidth integrates
- [[Sampling and Aliasing]] — bandwidth sets the sample rate, carrier doesn't
- [[SNR and Averaging]] — the √B lever in daily use
- [[Johnson-Nyquist Noise]] / [[Amplifier Noise]] / [[Vacuum Fluctuations]] — noise ∝ B, down to the quantum floor
- [[Control Beyond PID]] — servo bandwidth and the waterbed
- [[Numerical Aperture and Spot Size]] — the spatial version
- [[Transfer Functions and Bode Plots]] — where the −3 dB convention lives

---
Source: Bracewell, *The Fourier Transform and Its Applications*; Horowitz & Hill, *The Art of Electronics*, Ch. 8 (noise bandwidth); Slepian, "On bandwidth," *Proc. IEEE* 64, 292 (1976) (the 2WT theorem)
