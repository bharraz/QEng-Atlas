#dsp #electronics

**A raw periodogram never converges — its variance equals its mean no matter how long you record. Welch's fix: chop the record into segments, window each, FFT, and average the powers.** You trade frequency resolution for a spectrum you can actually trust.

# Reference

**The problem:** one $N$-point periodogram of noise has ~100% relative error per bin; taking more data at fixed segmenting just adds finer bins, each still 100% uncertain. Averaging is not optional.

**Welch's method:** split the record into $K$ segments of length $L$ (typically 50% overlap), apply a Hann window to each, compute $|X|^2$, average, scale as in [[FFT in Practice]]:

$$
\hat{S}(f) = \frac{1}{K} \sum_{i=1}^{K} \frac{2\,|X_i(f)|^2}{f_s \sum_n w_n^2}
$$

$K$ = number of segments averaged; $L$ = samples per segment, so resolution is $\Delta f = f_s/L$ and total record is $\approx KL/2$ samples at 50% overlap; $X_i$ = windowed DFT of segment $i$. Two knobs pulling against each other on a fixed record: $L$ buys frequency resolution, $K$ buys estimator precision (fractional uncertainty $\approx 1/\sqrt{K_{\text{eff}}}$), and $KL$ is fixed — so halving the bin width doubles the noise on every point.

**The tradeoff knob is segment length $L$:** resolution is $f_s/L$, while the fractional uncertainty of each PSD point is roughly $1/\sqrt{K_\text{eff}}$. Fixed total record ⇒ longer segments = finer bins but noisier estimate. With 50% overlap and Hann, overlapping segments are weakly correlated, so you recover most of the doubled count: $K_\text{eff} \approx 1.9\times$ the non-overlapped number. Overlap beyond ~50–75% buys almost nothing.

**Practical recipe:** decide the lowest frequency you care about, set $L \gtrsim 10 f_s/f_\text{min}$ so that frequency isn't sitting in the first couple of (window-corrupted) bins, then average as many segments as the record allows. Quote the result in V/√Hz or units²/Hz and *say* it's one-sided.

**Gotchas:** detrend each segment (a DC offset or slow drift leaks a huge $1/f^2$-looking skirt across the low bins and masquerades as flicker noise); nonstationary data violates the whole framework — glitches contaminate every averaged segment, so inspect the time series first. For drifty data, [[Allan Variance]] is often the honest statistic instead.

> [!question]- Your Welch PSD shows a rising low-frequency slope. Real 1/f noise or artifact?
> Check: (1) detrending on? A linear drift alone makes a fake $1/f^2$ slope. (2) Does the slope continue when you lengthen segments, or does it flatten? Real 1/f persists to lower bins; leakage from DC/drift changes with segmenting. (3) Compare Allan deviation — flicker has a flat floor there.

# Connections

- [[Power Spectral Density]] — the underlying quantity, units, and one/two-sided conventions
- [[FFT in Practice]] — window choice, ENBW, and the scaling this method inherits
- [[Wiener-Khinchin Theorem]] — the stationarity assumption Welch quietly relies on
- [[Allan Variance]] — the complementary time-domain statistic when drift breaks stationarity

---
Source: Lyons, *Understanding Digital Signal Processing*, Ch. 11; Heinzel et al. DFT-spectra note for the scaling
