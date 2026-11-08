#optics #labwork

**Every light detector absorbs a photon and frees one electron, and one electron is too small a signal to register; each detector type is defined by how it multiplies that electron into something countable — a chain of dynodes in vacuum, an avalanche in a reverse-biased diode, a superconducting wire switching to its resistive state, or a multiplication register on a camera chip — and that choice sets its efficiency, its noise, how fast it can count, and how it is damaged.** Picking a detector means picking which of those drawbacks the measurement can tolerate.

# Reference

**What every detector is judged by:**

| Figure of merit | Meaning | Why it matters |
|---|---|---|
| detection efficiency $\eta$ | probability that a photon arriving at the detector produces a count: quantum efficiency × active-area fill × coupling | sets the photon budget; heralded two-photon schemes scale as $\eta^2$ |
| dark count rate | counts per second with no light: thermally emitted electrons or thermally generated carriers | the background under the dark state in fluorescence detection |
| dead time $\tau_d$ | time after a count during which the detector cannot register another | count-rate saturation; photon pairs closer than $\tau_d$ are lost |
| afterpulsing | probability that a count triggers a false count shortly afterwards (trapped carriers, ion feedback) | fake correlations at short delay |
| timing jitter | spread in the delay between photon arrival and output pulse | time resolution of correlation and time-bin measurements |
| active area | size of the sensitive region | whether light must be focused to tens of µm or can fill millimetres |
| read noise, excess noise (cameras) | electrons of noise added per readout; extra variance from random gain | which camera is better at a given light level |

**Count-rate saturation.** A detector that is blind for $\tau_d$ after every count records

$$
R_m = \frac{R}{1 + R\,\tau_d}
$$

- $R$ — true rate of photons that would be detected (s⁻¹)
- $R_m$ — measured count rate (s⁻¹)
- $\tau_d$ — dead time per count (s)

so the measured rate falls below the true rate once $R\tau_d$ approaches about 0.1, and saturates at $1/\tau_d$. Some detectors (passively quenched avalanche diodes) instead extend their dead time when hit during it, and their measured rate *falls* at very high flux.

**Picture:** an electron multiplier as a cascade: each stage turns one electron into several, so the gain grows geometrically, and the randomness of the first stages sets the noise.

**The options:**

| Detector | How it gets gain | Efficiency | Dark counts | Speed | Strengths | Drawbacks |
|---|---|---|---|---|---|---|
| photomultiplier tube (PMT) | photoelectron from a photocathode accelerated through a chain of dynodes, each emitting several electrons per incident one (~10⁶ total) | 20–40% in the blue and near-UV, falling in the red | tens to hundreds per second | ns pulses, counts to ~10⁷ s⁻¹ | large area, good UV response, low dark counts | modest efficiency; ruined by room light while biased; gain shifts in magnetic fields; needs high voltage |
| single-photon avalanche diode (SPAD) | silicon diode biased above breakdown: one carrier triggers a self-sustaining avalanche, which circuitry then quenches | 50–70% in the red and near-IR, lower in the blue, poor in the UV | ~10–1000 per second | dead time tens of ns; jitter ~50–500 ps | high efficiency in the visible, compact | small active area (tens to ~200 µm); saturates at ~10⁷ s⁻¹; afterpulsing; emits a faint flash when it fires |
| InGaAs SPAD | the same, in InGaAs for 0.9–1.7 µm | ~10–30% | high; usually gated | long dead times (µs) to suppress afterpulsing | telecom wavelengths without a cryostat | noisy and slow |
| superconducting nanowire (SNSPD) | an absorbed photon breaks superconductivity in a current-biased nanowire; the current diverts and produces a voltage pulse | can exceed 90% at its design wavelength | below 1 to ~100 per second | recovery ~10–100 ns; jitter tens of ps | highest efficiency, lowest jitter, visible to mid-IR | needs a ~1–3 K cryostat; fiber-coupled small area; polarization-dependent; can latch into the resistive state at high flux |
| EMCCD camera | charge collected in pixels, multiplied in a serial register before readout | up to ~90% (back-illuminated, visible); lower in the UV unless UV-coated | dominated by clock-induced charge | ~10–1000 frames/s (more with a region of interest) | single-photon sensitivity with spatial resolution | random multiplication adds excess noise (equivalent to halving efficiency); deep cooling needed; gain register ages under bright light |
| sCMOS / qCMOS camera | an amplifier in every pixel, no multiplication | ~70–95% | low; read noise ~0.3–2 electrons | 100s–1000s frames/s | fast, no excess noise | pixel-to-pixel offset and gain variation; read noise matters below ~1 photon per pixel |
| linear-mode avalanche photodiode (APD) | avalanche below breakdown, gain ~10–100 | 50–80% | — | up to GHz | weak but not single-photon signals at high bandwidth | excess noise from the random gain |
| photodiode + transimpedance amplifier | none: photocurrent read directly | 50–90% quantum efficiency | — | set by the amplifier | bright beams (nW to mW), linear over many decades | not single-photon: the amplifier sets the noise floor ([[Photodiode Circuits]]) |

**Which detector for which job:**

| Job | Usual choice | Why |
|---|---|---|
| fluorescence from a single emitter (atom, ion, molecule, color center) | PMT for UV and blue light; SPAD for visible and near-IR light | low dark counts and large area in the UV; higher efficiency in the visible |
| many emitters read out at once (atom or ion arrays), or any low-light imaging | EMCCD or sCMOS camera, or a fiber array onto detector arrays | needs spatial resolution |
| photon correlations, Hong–Ou–Mandel interference, heralding | SPADs or SNSPDs | efficiency and timing jitter |
| telecom-wavelength photons | SNSPD, or InGaAs SPAD without a cryostat | silicon does not absorb beyond ~1.1 µm |
| beam power, lock error signals, intensity noise | photodiode + transimpedance amplifier | linear, fast, cheap |

**In a state-detection histogram:** the bright state's counts are Poissonian with a mean set by scattering rate × collection fraction ([[Numerical Aperture and Spot Size]]) × $\eta$ × detection time; the dark state's counts are dark counts plus scattered laser light. The overlap of the two distributions sets the readout error ([[Binomial Errors in State Detection]]). Dark counts matter only through the dark-state histogram, and dead time only if the bright-state rate approaches $1/\tau_d$.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| counts with the detector covered | dark count rate; a rise points to temperature or a light leak |
| counts with the laser on but no atom or ion | scattered background, separate from detector dark counts |
| count rate against input power stepped with calibrated attenuators | linearity; a rate growing more slowly than the input is dead-time saturation |
| autocorrelation of one detector's counts under laser light | a bump at short delay is afterpulsing (laser light itself is uncorrelated) |
| two-detector correlation under laser light | should be flat; a peak at the light-travel delay between the detectors is one SPAD seeing the other's avalanche flash |
| arrival-time histogram against a pulsed laser | timing jitter and any slow tail |

**Failure modes:**

| Failure | Mechanism | Prevention or symptom |
|---|---|---|
| PMT exposed to room light while biased | large photocurrent fatigues the photocathode and last dynodes, sometimes permanently | turn off the high voltage or close a shutter before opening enclosures; afterwards, raised dark counts and lowered gain |
| SPAD hit by a bright pulse | avalanche current heats the junction | gate the detector off during bright pulses; many modules shut down above a count-rate limit |
| SNSPD latching | at high flux or bias the wire stays resistive | counts stop until the bias is reset |
| EMCCD gain aging | high signal at high multiplication gain degrades the register | lower the gain before imaging bright light |
| magnetic field on a PMT | the field deflects electrons between dynodes | gain changes near coils, ion pumps, and isolator magnets; use a mu-metal shield |
| stray light | room light, laser scatter, and fluorescence from optics | baffles, bandpass filters, fiber coupling to the detector |

> [!question]- An EMCCD has effectively no read noise, yet an sCMOS camera with the same quantum efficiency gives better signal-to-noise at a few photons per pixel. Why?
> Electron multiplication is random, which doubles the variance of the amplified signal (excess noise factor $F^2 = 2$) — the same signal-to-noise as halving the quantum efficiency. At a few photons per pixel, the sCMOS read noise of about one electron adds less noise than that doubling, so sCMOS is better. The EMCCD is better only well below one photon per pixel per frame, where read noise would dominate.

# Connections

- [[Photodiode Circuits]] — the linear detector for bright light, and its amplifier
- [[Photodetection and Shot Noise]] — why counts are Poissonian and what efficiency does to noise
- [[Photon Statistics and g2]] — correlation measurements and why they use two detectors
- [[Binomial Errors in State Detection]] — turning count histograms into readout fidelity
- [[Numerical Aperture and Spot Size]] — how much light reaches the detector at all
- [[Semiconductors and Junctions]] — absorption, avalanche, and dark current in diodes
- [[Poisson Process]] — the statistics of counts and dark counts
- [[Hong-Ou-Mandel Interference]] — a measurement limited by detector efficiency and jitter
- [[Cryogenics]] — what an SNSPD needs to run
- [[Handling Lab Hardware]] — detector damage from light and static

---
Source: R. H. Hadfield, "Single-photon detectors for optical quantum information applications," *Nature Photon.* 3, 696 (2009); M. D. Eisaman et al., "Single-photon sources and detectors," *Rev. Sci. Instrum.* 82, 071101 (2011); Hamamatsu Photonics, *Photomultiplier Tubes: Basics and Applications*
