#dsp #electronics

**The FFT assumes your $N$ samples repeat forever — every practical gotcha (leakage, windows, scaling) comes from making that assumption less wrong.** This is the workhorse card: what to check when the spectrum looks weird.

# Reference

**Bin spacing** is $\Delta f = f_s/N$: record length sets resolution, sample rate sets span. Want 1 Hz resolution? You need 1 s of data, period.

**Leakage:** a tone that doesn't complete an integer number of cycles in the record has a discontinuity at the wrap-around, and its power smears into all bins (sinc-shaped skirts, falling only 6 dB/octave). Fix by **windowing** — taper the record edges to zero.

| Window | Main-lobe width | Highest sidelobe | ENBW (bins) | Use when |
|---|---|---|---|---|
| Rectangular (none) | 1 bin | −13 dB | 1.00 | exactly periodic / transient data |
| Hann | 2 bins | −31 dB | 1.50 | **default for everything** |
| Blackman-Harris | 4 bins | −92 dB | 2.00 | small tone next to big tone |
| Flat-top | 5 bins | −93 dB | 3.77 | accurate amplitude readout |

**Zero-padding interpolates the display; it adds no information.** Padding to $4N$ gives you a smoother curve through the same underlying spectrum — peak positions read off more easily, but resolution (ability to split two tones) is still set by the original record length.

**PSD scaling — where everyone gets burned.** For a one-sided PSD in V²/Hz from a windowed FFT $X_k$ with window $w_n$:

$$
S_{xx}(f_k) = \frac{2\,|X_k|^2}{f_s \sum_n w_n^2}
$$

where the window power $\sum w_n^2$ replaces the naive $N$. The **equivalent noise bandwidth** $\mathrm{ENBW} = f_s \frac{\sum w_n^2}{(\sum w_n)^2}$ is the effective width of one bin: to quote a noise floor in V/√Hz you divide bin power by ENBW, and to convert a *tone's* PSD bin back to power you multiply by it. Amplitude of a tone and density of noise scale differently — check with a known sine + known resistor's Johnson noise ([[Johnson-Nyquist Noise]] gives you a calibrated 4 nV/√Hz source for free).

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
