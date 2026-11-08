#dsp #electronics

**A signal sampled at a rate $f_s$ is known only at discrete times, and any frequency above $f_s/2$ produces exactly the same samples as a lower one** — the spectrum gets folded like an accordion at multiples of the Nyquist frequency, and once folded, the alias is indistinguishable from a real signal.

# Reference

**Nyquist:** a signal band-limited to $B$ is fully reconstructable if $f_s > 2B$. The information limit is real; the "sample at 10× to be safe" habit is about filter realizability, not information.

**Where an alias lands:** input at $f$ appears at

$$
f_\text{alias} = \left| f - n f_s \right|, \quad n = \mathrm{round}(f/f_s)
$$

- $f$ — true input frequency (Hz)
- $f_s$ — sample rate (samples/s)
- $n$ — the multiple of $f_s$ nearest to $f$ ($n = 0$ for inputs below $f_s/2$)
- $f_\text{alias}$ — where the input appears in the sampled data (Hz), always inside $[0, f_s/2]$

In words: subtract the nearest multiple of $f_s$, which is the same as reflecting the frequency off $f_s/2$ until it lands inside $[0, f_s/2]$. A 1.1 MHz tone sampled at 1 MSa/s shows up at 100 kHz, indistinguishable from a real 100 kHz tone. The folding comes from sampling itself: taking samples multiplies the signal by an impulse train, whose Fourier transform is another impulse train of spacing $f_s$ ([[Fourier Transform]]), so the spectrum is *convolved* with that comb and every shifted copy overlaps the band you keep.

**Picture:** a wagon wheel in a film: filmed at a fixed frame rate, a wheel spinning fast enough appears to turn slowly or backwards.

**The anti-alias filter must be analog and must come before the ADC.** After sampling, the alias *is* the data — no digital filter can unmix it. Practical consequence: your filter's stopband must be down by the time you reach $f_s - f_\text{max}$, which is why oversampling then decimating digitally is so popular (relaxes the analog filter to a gentle roll-off).

**Aliased noise:** aliasing isn't always obvious tones. Broadband noise above Nyquist folds down and raises your noise floor — an unfiltered ADC input can look "noisy" when it's really aliased RF pickup. Also true for scope measurements: a scope in equivalent-time or low sample-rate mode will readily alias your RF drive into a fake slow oscillation.

**Undersampling as a feature:** if the signal is band-limited to a narrow band around a high carrier (e.g. an IF at 70 MHz, 1 MHz wide), you can deliberately sample below the carrier and let the fold-down do your downconversion — the band has to fit in one Nyquist zone (one of the bands between successive multiples of $f_s/2$). This is how many RF digitizers and [[Direct Digital Synthesis]]-adjacent receivers work.

> [!question]- You see a clean 100 kHz line in your sampled data (1 MSa/s) that no analog probe can find. What frequencies could it really be?
> Anything that folds to 100 kHz: 0.9, 1.1, 1.9, 2.1 MHz, … i.e. $n f_s \pm 100$ kHz. Check by changing $f_s$ slightly — a real 100 kHz line stays put, an alias moves.

# Connections

- [[ADC and DAC Realities]] — the hardware where sampling happens, plus quantization and jitter
- [[FFT in Practice]] — aliased content shows up as inexplicable spectral lines in your FFT
- [[Fourier Transform]] — sampling = multiplying by a comb, which convolves the spectrum with a comb: the folding, derived
- [[RC and RL Filters]] — the simplest anti-alias filters, and why one pole is rarely steep enough

---
Source: Lyons, *Understanding Digital Signal Processing*, Ch. 2
