#dsp #electronics

**Converters are specified in bits but perform in effective bits — quantization sets an ideal noise floor, and jitter, nonlinearity, and reference noise eat it from there.** Know the ideal numbers so you can tell when the hardware (or your layout) is underperforming.

# Reference

**Quantization noise:** an ideal $N$-bit ADC spanning $V_\text{FS}$ has step $q = V_\text{FS}/2^N$ and adds noise of variance $q^2/12$, spread white across $[0, f_s/2]$. Ideal SNR for a full-scale sine:

$$
\mathrm{SNR} = 6.02\,N + 1.76 \ \text{dB}
$$

**ENOB** is that equation run backwards on the *measured* SINAD: a "16-bit" ADC delivering 78 dB is really 12.7 effective bits. Datasheets quote ENOB at specific frequencies — it degrades as input frequency rises.

**Oversampling & processing gain:** the quantization noise power is fixed, so spreading it over more bandwidth and filtering to your signal band buys $10\log_{10}(f_s/2B)$ dB — 3 dB (half a bit) per octave of oversampling. Sigma-delta converters push this to extremes.

**Dither:** quantization error is only noise-like if the signal exercises many codes. Small, slow signals produce distortion (dead zones, harmonics), not noise. Adding ~1 LSB of noise before the ADC *linearizes* the average — you can then average below the LSB. Often your signal chain is already noisy enough; if it isn't, add dither on purpose.

**Jitter:** timing noise $\sigma_t$ on the sample clock converts slew rate into voltage noise, limiting SNR to $-20\log_{10}(2\pi f_\text{in}\sigma_t)$. At $f_\text{in}=10$ MHz, 1 ps rms jitter caps you at ~84 dB regardless of bits. This is why fast digitizers care so much about clock cleanliness — and why aliased clock spurs point at your clock distribution, not the ADC.

**DAC side:** a DAC's zero-order hold outputs stairsteps, which (1) roll off the wanted signal as $\mathrm{sinc}(f/f_s)$ — −3.9 dB at Nyquist, sometimes pre-compensated digitally — and (2) produce **images** of the signal around every multiple of $f_s$, attenuated only by that same sinc. The analog **reconstruction filter** after the DAC is not optional; unfiltered images will happily drive your AOM or mix down in a later stage. Glitch energy at major code transitions is the other classic DAC wart.

> [!question]- Your 16-bit DAC updates at 1 MSa/s generating a 10 kHz sine for a coil driver. What's sitting at 990 kHz and how big?
> The first image ($f_s - f$), attenuated only by $\mathrm{sinc}(0.99) \approx -40$ dB relative to the fundamental. Without a reconstruction filter that's a real, large spur — filter it or move $f_s$ up.

# Connections

- [[Sampling and Aliasing]] — the other half of the conversion story; anti-alias in, reconstruction out
- [[Direct Digital Synthesis]] — DDS output quality is exactly DAC images + sinc + spurs
- [[FFT in Practice]] — how to actually measure ENOB, floors, and spurs on the bench
- [[Johnson-Nyquist Noise]] — compare the quantization floor to your analog front end's thermal floor; the bigger one wins
- [[Shot Noise]] — for photodetector chains, check whether ADC noise or shot noise limits you

---
Source: Analog Devices, *The Data Conversion Handbook* (Kester), Ch. 2; Lyons Ch. 12
