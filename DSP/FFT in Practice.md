#dsp #electronics

**The FFT assumes your $N$ samples repeat forever — every practical gotcha (leakage, windows, scaling) comes from making that assumption less wrong.** This is the workhorse card: what to check when the spectrum looks weird.

# Reference

**Bin spacing** is $\Delta f = f_s/N$: record length sets resolution, sample rate sets span. Want 1 Hz resolution? You need 1 s of data, period.

**Leakage:** a tone that doesn't complete an integer number of cycles in the record has a discontinuity at the wrap-around, and its power smears into all bins (sinc-shaped skirts, falling only 6 dB/octave). Fix by **windowing** — taper the record edges to zero.

| Window | Highest sidelobe | ENBW (bins) | Use when |
|---|---|---|---|
| Rectangular (none) | −13 dB | 1.00 | exactly periodic / transient data |
| Hann | −31 dB | 1.50 | **default for everything** |
| Blackman-Harris | −92 dB | 2.00 | small tone next to big tone |
| Flat-top | −93 dB | 3.77 | accurate amplitude readout |

Full table with main-lobe widths, sidelobe rolloff rates, and scalloping loss — plus why the rolloff rate is set by edge smoothness — is in [[Window Functions and Apodization]].

**Zero-padding interpolates the display; it adds no information.** Padding to $4N$ gives you a smoother curve through the same underlying spectrum — peak positions read off more easily, but resolution (ability to split two tones) is still set by the original record length.

**PSD scaling — where everyone gets burned.** For a one-sided PSD in V²/Hz from a windowed FFT $X_k$ with window $w_n$:

$$
S_{xx}(f_k) = \frac{2\,|X_k|^2}{f_s \sum_n w_n^2}
$$

$X_k$ = the windowed DFT output at bin $k$ (V, unnormalized as most libraries return it); $w_n$ = window coefficients (dimensionless, $w_n = 1$ for no window); $f_s$ = sample rate (Sa/s); the 2 folds negative frequencies into a one-sided density. The denominator $f_s\sum w_n^2$ is what carries the units: $\sum w_n^2$ replaces the naive $N$ because a taper removes effective samples, and dividing by $f_s$ turns per-bin power into per-Hz density.

$$\mathrm{ENBW} = f_s\,\frac{\sum_n w_n^2}{\left(\sum_n w_n\right)^2}$$

= the effective width of one bin (Hz) — the bandwidth a brick-wall filter would need to pass the same noise power as this window's bin. Divide bin power by ENBW for a noise floor in V/√Hz; multiply by it to recover a *tone's* total power. Tones and noise scale differently precisely because a tone occupies one bin regardless of window while noise fills all of them. Amplitude of a tone and density of noise scale differently — check with a known sine + known resistor's Johnson noise ([[Johnson-Nyquist Noise]] gives you a calibrated 4 nV/√Hz source for free).

**Averaging:** power averaging ($\langle |X|^2 \rangle$, Welch-style) reduces the variance of the spectrum estimate but the noise floor stays put; **coherent averaging** (average the complex $X_k$, needs a phase-stable trigger) pulls signals out of the noise, floor drops by $1/\sqrt{N_\text{avg}}$.

> [!question]- Your tone's measured amplitude drops 1.4 dB when you move its frequency half a bin. Bug?
> No — scalloping loss. The tone sits between bins and Hann's main lobe isn't flat. Use a flat-top window (or interpolate across the 3 nearest bins) for amplitude accuracy.

# Connections

- [[Power Spectral Density]] — the quantity the scaled FFT estimates; units and one/two-sided conventions live there
- [[Sampling and Aliasing]] — mystery lines in the FFT are often folds, not signals
- [[PSD Estimation]] — Welch averaging, the right way to quote a spectrum from noisy data
- [[Fourier Transform]] — the continuous ideal this discretizes; the key transform pairs
- [[Wiener-Khinchin Theorem]] — why $|X|^2$ estimates the PSD at all

---
Source: Lyons, *Understanding Digital Signal Processing*, Ch. 3; Heinzel et al., "Spectrum and spectral density estimation by the DFT" (the definitive scaling note)
