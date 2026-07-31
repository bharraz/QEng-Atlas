#dsp #math #optics #quantum

**Any finite measurement, pulse, or aperture multiplies the true signal by a window, and multiplication in one domain is convolution in the other — so the window's own transform is smeared over everything you observe.** Choosing a window is choosing where to sit on one unavoidable trade: a narrow main lobe (resolution) against low sidelobes (dynamic range). The same choice appears as spectral leakage, filter ripple, off-resonant excitation, diffraction rings, and decoupling-sequence design.

# Reference

Observing $x(t)$ through a window $w(t)$ of duration $T$:

$$x_{\text{obs}}(t) = w(t)\,x(t) \qquad \Longleftrightarrow \qquad X_{\text{obs}}(f) = (W * X)(f).$$

$w$ = window (dimensionless envelope, 1 inside and tapering to 0 at the edges); $W$ = its Fourier transform, the **kernel** smeared over the true spectrum. Every artifact follows from the shape of $W$:

- **Main-lobe width** $\sim 1/T$ sets resolution — two features closer than this merge. No window beats the $1/T$ scaling ([[Bandwidth]]); windows only change the prefactor.
- **Sidelobes** set dynamic range — a strong feature leaks energy at the sidelobe level into distant bins, masking weak features there.
- **Sidelobe asymptotic rolloff is set by smoothness at the edges**: if $w$ is discontinuous in value, sidelobes fall as $1/f$ (−6 dB/octave); discontinuous first derivative gives $1/f^2$ (−12 dB/oct); Hann is continuous in value *and* derivative at the edges and falls at −18 dB/oct. This is the one structural rule — everything else is a table.

Widening the main lobe is what buys lower sidelobes, and the product of the two cannot be improved past the Slepian (DPSS) optimum, which is the precise statement of the trade.

## The table

Main-lobe width in DFT bins (null-to-null), ENBW in bins, scalloping = worst-case amplitude error for a tone between bins:

| Window | Main lobe | Peak sidelobe | Rolloff | ENBW | Scalloping | Use |
|---|---|---|---|---|---|---|
| Rectangular (none) | 2 | −13 dB | −6 dB/oct | 1.00 | 3.9 dB | exactly periodic data, transients |
| Hann | 4 | −31 dB | −18 dB/oct | 1.50 | 1.4 dB | general default |
| Hamming | 4 | −43 dB | −6 dB/oct | 1.36 | 1.8 dB | lowest *nearest* sidelobe |
| Blackman | 6 | −58 dB | −18 dB/oct | 1.73 | 1.1 dB | better dynamic range |
| Blackman–Harris (4-term) | 8 | −92 dB | −6 dB/oct | 2.00 | 0.8 dB | weak tone beside a strong one |
| Flat-top | 10 | −93 dB | — | 3.77 | <0.01 dB | accurate amplitude readout |
| Kaiser / DPSS | tunable $\beta$ | tunable | — | tunable | — | when you want to *specify* the trade |
| Gaussian (untruncated) | — | none | — | — | — | the ideal: no sidelobes at all |

Two rows deserve attention. **Hamming vs Hann**: Hamming cancels the first sidelobe by construction (−43 dB) but leaves a discontinuous edge, so its far sidelobes decay only at −6 dB/oct — Hann is worse nearby and much better far away. Pick by where your interferer sits. **Flat-top** deliberately spends enormous main-lobe width to make the peak flat, so a tone anywhere between bins reads its true amplitude — the right choice when calibrating a level, the wrong one when resolving two lines.

## Where the same choice appears

**Spectral analysis.** The classic case: a record of length $T$ *is* a rectangular window, so leakage exists whether or not you apply a taper. Scalloping loss, ENBW corrections, and Welch's per-segment windowing all live here ([[FFT in Practice]], [[PSD Estimation]]).

**FIR filter design.** An ideal brick-wall filter has a sinc impulse response of infinite length; truncating it is windowing, and the window's sidelobes become the filter's stopband ripple. Rectangular truncation gives the Gibbs overshoot; Hamming or Kaiser windows are the standard fix, trading transition width for stopband attenuation — the same trade under a different name ([[Digital Filters]]).

**Pulse shaping in quantum control.** A square pulse of duration $T$ is a rectangular window on the carrier, so its excitation profile is a sinc with −13 dB sidelobes hundreds of kHz away — off-resonant excitation of spectator transitions or neighbouring ions. Replacing the envelope with a Gaussian or Blackman removes the sidelobes entirely at the cost of a wider main lobe (a longer pulse for the same selectivity). This is why shaped pulses exist in [[Optical Tweezers|addressed]] and multi-level systems, and it is the same reasoning behind DRAG for weakly anharmonic qubits ([[Superconducting Qubits]], [[Fourier Transform]]).

**Optical apodization.** A hard aperture is a two-dimensional rectangular window, and its transform is the Airy pattern — the rings are literally sidelobes. Truncating a Gaussian beam at a finite aperture interpolates between the ringed and ring-free extremes, which is why single-atom addressing crosstalk is set by aperture truncation and aberration rather than by the ideal spot size ([[Numerical Aperture and Spot Size]], [[Diffraction]]).

**Dynamical decoupling.** A pulse sequence defines a modulation $y(t) = \pm1$ over the interrogation time — a window in the most literal sense, taking values rather than tapering. Its transform *is* the filter function that overlaps the noise spectrum, so sequence design is window design: CPMG is a square-wave window (narrow passband, harmonics at odd multiples), UDD optimizes pulse *spacing* the way Kaiser optimizes taper shape, and phase-alternating families like XY-8 shape the window to reject pulse errors as well as noise ([[Spin Echo and Dynamical Decoupling]], [[Noise Spectroscopy and Filter Functions]]).

**Boxcar and gated detection.** Integrating a detector over a gate is a rectangular window in time; its transform is the frequency response of the gate, and interference at the gate's sidelobe frequencies leaks in accordingly.

> [!question]- A small spectral feature 60 dB below a strong nearby tone is invisible with a Hann window and appears with Blackman–Harris. Is it real, and what did the window change?
> Likely real, and the window changed the sidelobe floor, not the resolution. Hann's −31 dB peak sidelobe means the strong tone's leakage is smearing at roughly that level across neighbouring bins, burying anything below it; Blackman–Harris drops that floor to −92 dB at the price of a main lobe four times wider. Confirm by a test that does not depend on the window: change the record length (a real feature stays at the same frequency and its width scales as $1/T$; a leakage artifact moves with the window and the tone's bin offset), or change the sample rate to move any aliased candidate ([[Sampling and Aliasing]]).

# Connections

- [[FFT in Practice]] — spectral leakage, scalloping, and the scaling that ENBW enters
- [[PSD Estimation]] — Welch windowing and the resolution-vs-variance trade
- [[Bandwidth]] — the $1/T$ main-lobe scaling as one more face of the time–bandwidth limit
- [[Fourier Transform]] — multiplication ↔ convolution, and the rect/Gaussian pair driving everything here
- [[Digital Filters]] — windowed-sinc FIR design; Gibbs ripple as sidelobes
- [[Spin Echo and Dynamical Decoupling]] / [[Noise Spectroscopy and Filter Functions]] — sequences as windows, filter functions as their transforms
- [[Numerical Aperture and Spot Size]] / [[Diffraction]] — apertures as spatial windows; Airy rings as sidelobes

---
Further reading: Harris, "On the use of windows for harmonic analysis with the discrete Fourier transform," *Proc. IEEE* 66, 51 (1978) — the definitive table; Heinzel, Rüdiger & Schilling, "Spectrum and spectral density estimation by the DFT" (2002) — scaling conventions; Slepian, "Prolate spheroidal wave functions V," *Bell Syst. Tech. J.* 57, 1371 (1978) — the optimal concentration trade
