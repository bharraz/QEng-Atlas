#dsp #electronics

**Two species: FIR filters convolve with a finite kernel (always stable, exactly linear phase, but need many taps), IIR filters feed output back (cheap and steep, but they distort phase and can ring or go unstable).** Pick FIR when the waveform shape matters, IIR when you just need the band gone.

# Reference

| | FIR | IIR |
|---|---|---|
| Structure | $y_n = \sum_k b_k x_{n-k}$ | adds $\sum_k a_k y_{n-k}$ feedback |
| Stability | unconditional | poles must stay inside unit circle |
| Phase | exactly linear (symmetric taps) → pure delay | nonlinear, worst near cutoff |
| Cost for sharp cutoff | hundreds of taps | a few biquads |
| Analog ancestry | none | Butterworth/Chebyshev/Bessel via bilinear transform |

**Latency:** an $N$-tap linear-phase FIR delays by $N/2$ samples — this is what kills FIR inside feedback loops ([[PID Control]] loops want minimum-phase, low-latency IIR or plain analog). IIR delay is smaller but frequency-dependent.

**The moving average is a lousy low-pass:** its response is a sinc — first sidelobe only −13 dB, and it *passes* signals near the nulls' edges while notching others. Fine for decimation-by-averaging or killing one known frequency (put the null on 60 Hz), wrong as a general anti-noise filter. A windowed-sinc FIR or a 2nd-order Butterworth biquad costs little more and behaves.

**filtfilt (zero-phase trick):** run the IIR forward, then backward over the record. Phase distortion cancels exactly, magnitude response applies twice. Offline analysis only — it's acausal, so never in a live loop. Watch the edges: the filter rings into the start/end of your data.

**Design in practice:** you specify passband, stopband, ripple; `scipy.signal` (remez/firwin for FIR, butter/cheby for IIR) hands you coefficients. Implement IIR as cascaded second-order sections (SOS), not one high-order polynomial — direct high-order forms blow up numerically.

> [!question]- Why does filtering your ringdown trace with a 4th-order Butterworth change the fitted decay time, while the equivalent FIR doesn't?
> IIR phase distortion smears the transient asymmetrically (and the filter's own impulse response convolves into the decay). Linear-phase FIR just shifts the trace by a known constant delay. For pulse/transient shapes, use FIR or Bessel-like responses — or fit with the filter included in the model.

# Connections

- [[Filter Families]] — Butterworth/Chebyshev/Bessel tradeoffs carry straight over to IIR designs
- [[FFT in Practice]] — check your filter did what you think by looking at the before/after spectrum
- [[Convolution]] — FIR filtering *is* convolution; impulse response = the tap vector
- [[PID Control]] — where filter latency and phase lag become loop stability problems

---
Source: Lyons, *Understanding Digital Signal Processing*, Ch. 5–6
