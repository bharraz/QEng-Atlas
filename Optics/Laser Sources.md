#optics #labwork

**The light at a particular atomic line rarely comes from one box: a gain medium — a semiconductor chip, a doped crystal or fiber — amplifies light near some wavelength, a cavity or grating picks one frequency out of its gain band, an amplifier adds power, and a nonlinear crystal converts the frequency when no gain medium reaches the line directly.** Each stage brings its own way of drifting or failing, so a laser system is debugged stage by stage.

# Reference

**Sources by gain medium:**

| Source | How it works | Typical output | Strengths | Drawbacks |
|---|---|---|---|---|
| bare (Fabry–Pérot) diode | the chip's cleaved facets are the cavity mirrors | multimode, mW–W | cheap; tuned and modulated by current | many longitudinal modes; wavelength drifts with temperature and current |
| DFB or DBR diode | a grating written into the chip selects one mode | single-mode, ~MHz linewidth, nm of tuning by temperature | robust, no alignment | linewidth too broad for narrow transitions; limited wavelength choice |
| external-cavity diode laser (ECDL) | diode with an anti-reflection-coated facet and feedback from an external grating ([[Diffraction Gratings]]) or interference filter | single-mode, ~100 kHz free-running linewidth, tunable over nm | narrow and tunable: the standard laser for atomic lines | mode hops; sensitive to feedback, vibration, and temperature; alignment drifts |
| tapered amplifier (TA) | a diode chip whose gain stripe widens along its length amplifies a seed beam in one pass | 0.5 to several W | power with the seed's spectrum | poor, astigmatic beam (fiber coupling ~50–60%); broadband amplified spontaneous emission (ASE) background; destroyed if run unseeded or by back-reflection |
| injection-locked diode | a free-running diode seeded by a weak master laser takes the master's frequency | tens to hundreds of mW | cheap power with a clean spectrum | locks only over a limited current and temperature range; unlocks silently |
| fiber laser or amplifier (Yb-, Er-doped) | diode-pumped doped fiber | W to kW near 1.0–1.1 µm and 1.5–1.6 µm | power, good beam, narrow linewidth from a narrow seed | only at those bands; stimulated Brillouin scattering limits narrow-line power |
| Ti:sapphire | crystal pumped by green light | 650–1100 nm at W level, widely tunable; mode-locked versions give fs pulses | tunability and power | expensive; needs a pump laser and active stabilization |
| diode-pumped solid-state (DPSS) | Nd- or Yb-doped crystal pumped by diodes, often frequency-converted | fixed lines (1064, 532, 355 nm), CW or pulsed | high power at fixed wavelengths | no tuning |
| mode-locked laser | many longitudinal modes locked in phase emit a pulse train, a frequency comb | pulses from ps to fs | [[Frequency Combs]]; Raman gates driven by pulsed light (355 nm for Yb⁺) | complex; broadband by design |

**Tuning a diode laser.** Temperature and current both move two things at different rates: the gain peak of the chip, and the frequencies of the cavity modes. The laser runs on whichever cavity mode has the most net gain, so as the gain peak moves relative to the modes, a neighbouring mode eventually takes over and the frequency jumps — a **mode hop**. In an ECDL the grating sets the selected frequency; a piezo changes the grating angle and cavity length together, and feeding part of the piezo signal forward to the diode current keeps the cavity mode tracking the grating, extending the range that scans without hopping. A map of wavelength against current and temperature shows the stable single-mode regions.

**Frequency conversion.** Second-harmonic generation (SHG) combines two photons at $\omega$ into one at $2\omega$ in a nonlinear crystal; at low conversion

$$
P_{2\omega} = \eta_\text{SHG}\, P_\omega^2
$$

- $P_\omega$ — fundamental power entering the crystal (W)
- $P_{2\omega}$ — second-harmonic power out (W)
- $\eta_\text{SHG}$ — conversion coefficient (W⁻¹): set by crystal, length, and focusing

Because output grows as the square of input, doubling needs high power: either a single pass with a fiber amplifier or TA, or an enhancement cavity around the crystal, locked to the laser, that multiplies the circulating power ([[Fabry-Perot Cavity]]). The crystal must be phase-matched — angle- or temperature-tuned for birefringent crystals (BBO, LBO), or periodically poled (PPLN, PPKTP). Sum-frequency generation combines two different lasers the same way. Direct diodes now reach many ion lines in the violet and blue and most repumpers in the red and infrared; deep-UV lines (Be⁺ 313 nm, Mg⁺ 280 nm) come from doubling or quadrupling.

**Picture:** the gain medium sets where in the spectrum you can be, the cavity or grating sets exactly where you are, and the amplifier and converter carry that choice to the power and wavelength the experiment needs.

**Bringing up a stage — what to check, in order.** Before connecting a laser to anything else, establish:

1. power against current (threshold, slope, kinks);
2. single-mode operation on a scanning cavity;
3. the wavelength on a wavemeter;
4. only then, locking and amplification.

Each later stage inherits the faults of the one before, so a fault found at stage three is easiest to fix at stage one.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| power against current (L–I curve) | threshold and slope; kinks are mode hops or feedback |
| wavemeter | absolute wavelength — but multimode light is silently averaged ([[Lab Instruments]]) |
| scanning Fabry–Pérot | whether the laser is single-mode, side modes, hops during a scan |
| beat note against another laser or a comb | linewidth and frequency noise ([[Laser Linewidth]]) |
| grating optical spectrum analyzer | side-mode suppression and the broadband ASE pedestal of amplifiers |

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| mode hop | drift moves the selected cavity mode off the feedback or gain maximum | sudden GHz-scale frequency jump, power step, lost lock |
| multimode operation | feedback too weak or misaligned | jumping or averaged wavemeter reading; several peaks on a scanning cavity |
| optical feedback | a back-reflection forms an extra cavity ([[Optical Isolators]]) | broadened linewidth, noise, hops that depend on downstream alignment |
| facet damage | intensity at the output facet exceeds its limit | permanent power drop |
| electrical damage | reverse voltage, static discharge, or current spikes ([[Handling Lab Hardware]]) | dead or dimmed diode, raised threshold |
| unseeded or back-reflected TA | full gain with no seed to deplete it | permanent damage to the chip |
| ASE background | amplifiers emit broadband spontaneous emission | light far from the laser line that can drive other transitions; filter it |
| condensation | the temperature controller cools the diode below the dew point | water on the chip, then damage |
| nonlinear-crystal degradation | UV damage, moisture (BBO is slightly hygroscopic), photorefractive effects in lithium niobate | falling conversion efficiency, distorted output beam |

> [!question]- A diode laser mode-hops when only its temperature is changed. Why does temperature alone make the frequency jump?
> Temperature moves the gain peak and the cavity modes at different rates. The laser always runs on the cavity mode with the most net gain; as the gain peak drifts relative to the mode comb, a neighbouring mode overtakes the current one, and the frequency jumps by one mode spacing. Continuous tuning needs the gain peak, the frequency-selective feedback, and the cavity mode to move together.

# Connections

- [[Laser Fundamentals]] — gain, threshold, and mode selection
- [[Laser Linewidth]] — what limits the purity of a single-mode source
- [[Diffraction Gratings]] — grating feedback in the ECDL
- [[Optical Isolators]] — protection from feedback
- [[Fabry-Perot Cavity]] — scanning cavities and doubling cavities
- [[Frequency Combs]] — mode-locked lasers as frequency rulers
- [[Pound-Drever-Hall Locking]] — locking a source to a cavity
- [[Saturated Absorption Spectroscopy]] — locking a source to an atomic line
- [[Photon Detectors]] — the other end of the beam
- [[Handling Lab Hardware]] — how diodes and amplifiers are damaged in handling
- [[Intensity Stabilization]] — stabilizing the power a source delivers

---
Source: C. E. Wieman & L. Hollberg, "Using diode lasers for atomic physics," *Rev. Sci. Instrum.* 62, 1 (1991); Siegman, *Lasers*; Boyd, *Nonlinear Optics*, Ch. 2
