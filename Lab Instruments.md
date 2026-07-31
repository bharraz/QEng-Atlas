#labwork #reference

**Every instrument answers one question well and lies about the others. The failure mode is not reading the display wrong — it is a setting that silently changes what the display means.** Organized as: what it measures, the settings that lie to you, and when to reach for something else.

# Reference

## Oscilloscope — voltage vs time

**Two separate specs, both matter.** Analog bandwidth $f_{3\text{dB}}$ sets what the front end passes; sample rate $f_s$ sets what the digitizer records. You need *both*: $f_s \geq 5f_{3\text{dB}}$ or the display aliases within the scope's own passband. Rise time you can resolve $\approx 0.35/f_{3\text{dB}}$ ([[Bandwidth]]), and measured rise time is $\sqrt{t_{r,\text{signal}}^2 + t_{r,\text{scope}}^2}$ — a scope of comparable speed to the signal reports an edge ~40% too slow.

**Settings that lie:**

- **50 Ω vs 1 MΩ input** — changes both the amplitude ($V = IR$) and the bandwidth ($\tau = RC$ with cable capacitance) of anything with source impedance ([[Time Constants and Reactance Rules of Thumb]]). A signal that "disappears" on 50 Ω was being integrated by the 1 MΩ input.
- **Probe compensation** — an uncompensated 10× probe distorts every edge; square-wave the cal output and adjust before trusting any risetime. Probe loading (~10 pF) is part of your circuit.
- **AC coupling** removes DC *and* rolls off below ~10 Hz — slow drift vanishes silently.
- **Acquisition mode**: "peak detect" catches glitches but exaggerates noise; "average" hides single events entirely; "high-res" trades bandwidth for bits. A noise measurement in average mode is meaningless.
- **Memory depth vs timebase**: at a long timebase the scope drops $f_s$ to fill the record — you can be aliasing at slow sweeps while the front end is fast.
- **Trigger**: edge triggering shows you only the events you already expected. Pulse-width, runt, dropout, and logic-pattern triggers exist to catch the failure you cannot see ([[Debugging Method]] rule 3).

**Reach for something else when:** you need the frequency content (spectrum analyzer), sub-µV sensitivity (lock-in), phase noise (analyzer or PLL), or absolute frequency (counter/wavemeter).

## Spectrum analyzer — power vs frequency

A swept superheterodyne: it mixes a band down and measures power through a filter of width RBW. Modern FFT-based analyzers compute the same picture from samples.

**Settings that lie:**

- **RBW** sets both resolution *and* the displayed noise floor: floor $\propto$ RBW, so narrowing RBW by 10× drops the noise floor 10 dB and makes weak spurs "appear." Always state RBW alongside a noise-floor number.
- **VBW** is post-detector smoothing — it makes the trace look cleaner without improving anything real; VBW < RBW/3 smooths noise but also suppresses genuine fast-varying features.
- **Sweep time** is coupled: $T_{\text{sweep}} \gtrsim \mathrm{span}/\mathrm{RBW}^2$. If the analyzer is sweeping too fast for the RBW, peaks are *attenuated and shifted* — the "uncal" warning exists for this.
- **Reference level** sets front-end attenuation. Too low and the input compresses, generating intermodulation spurs *inside the analyzer* that look like real signals. Test: raise the attenuation by 10 dB — real signals stay put, internally generated ones drop.
- **Detector mode** (peak / sample / RMS): peak overestimates noise, RMS is the correct choice for noise density measurements.
- A **tracking generator** turns it into a scalar network analyzer — magnitude only, no phase.

**Reach for something else when:** you need phase (VNA), absolute frequency to Hz (counter), or the signal is below the analyzer's noise floor (lock-in, or amplify first — [[Amplifier Noise]]).

## Vector network analyzer — S-parameters vs frequency

Magnitude *and* phase of reflection and transmission ([[S-Parameters]]).

- **Calibration defines the reference plane.** SOLT/electronic cal at the front panel measures your cables as part of the DUT; calibrate at the connector that actually touches the device. Recalibrate after changing IF bandwidth, power, or frequency range.
- **Port power** matters for nonlinear or superconducting devices — measure a resonator's $Q$ versus power, since it will change.
- Reflection-only ($S_{11}$) measurements need a good load standard; a mediocre load sets a floor on measurable return loss.
- Use it for: filter and cable characterization, resonator $Q$ ([[Resonance and Q Factor]] — remember it measures *loaded* $Q$), impedance matching ([[Impedance Matching]]), and finding cable faults via time-domain transform.

## Frequency counter

Counts cycles against a reference over a gate time $T$: resolution $\approx 1/T$ for a simple counter, far better for reciprocal/interpolating counters.

- **Accuracy is the timebase's, not the counter's** — a 10 MHz OCXO at $10^{-9}$ caps you there; discipline to GPS or a maser for better.
- **It lies on noisy or multi-tone signals**: a counter reports *a* number even when the input is a mess. Look at the signal on a scope or analyzer first, and use the trigger-level and low-pass filter controls deliberately.
- Frequency instability is a curve, not a number — pipe the readings into [[Allan Variance]] rather than quoting one measurement.

## Multimeter

- **True-RMS vs average-responding**: average-responding meters are calibrated for sines and read low on anything else (pulsed, chopped, or crest-factor-heavy signals). Check which you have.
- **Burden voltage**: measuring current inserts a shunt whose IR drop can be tens of mV — enough to change a bias point.
- **Input impedance** is 10 MΩ typically; on a high-impedance node that is a load, and on a floating node the reading is meaningless.
- Bandwidth is DC to a few kHz — a DMM cannot tell you about anything fast, and a "clean DC" reading says nothing about the RF riding on it.

## Optical instruments

- **Power meter**: thermal heads are slow (~s) but flat from UV to IR; photodiode heads are fast and sensitive but *wavelength-calibrated* — set the wavelength or the reading is simply wrong, and they saturate well below thermal heads.
- **Wavemeter**: absolute frequency to ~10 MHz–1 GHz depending on class. Multi-mode light gives a weighted average with no warning; check mode structure on a scanning cavity ([[Fabry-Perot Cavity]]) before trusting a wavemeter number.
- **Scanning Fabry–Perot**: shows mode structure and relative linewidth; features separated by an integer FSR alias on top of each other, so identify the FSR first.
- **Beam profiler**: reports $D4\sigma$ or $1/e^2$ or FWHM widths — three different numbers for the same beam ([[Conventions and Factor-of-Two Traps]]).

## Cross-checking

No single instrument is trustworthy alone. The cheap habits: measure a known signal before measuring an unknown one; verify a level two ways (scope and power meter, analyzer and counter); check that changing an instrument setting changes the reading the way theory says it should. A measurement that does not respond to a deliberate perturbation is often the instrument, not the physics.

> [!question]- A spectrum analyzer shows a −70 dBm spur that vanishes when you add a 10 dB input attenuator and re-normalize. Real or not?
> Not real — it was generated inside the analyzer. A genuine signal drops 10 dB with the attenuator and comes back to −70 dBm after you account for it; an intermodulation product created in a compressed front end drops by 20–30 dB because it scales as a higher power of the input level. This attenuator test is the standard discriminator, and it is worth running any time a spur appears near a strong carrier.

# Connections

- [[Debugging Method]] — rule 3 (look) and rule 7 (test the tool) in practice
- [[Bandwidth]] — the rise-time/bandwidth and ENBW relations these specs rest on
- [[Time Constants and Reactance Rules of Thumb]] — probe loading, 50 Ω vs 1 MΩ
- [[Sampling and Aliasing]] — why sample rate and analog bandwidth are separate specs
- [[S-Parameters]] / [[Impedance Matching]] — what the VNA measures and why
- [[Lock-In Detection]] — the instrument for signals below a spectrum analyzer's floor
- [[Conventions and Factor-of-Two Traps]] — which width, which dB, which impedance

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., App. O (oscilloscopes) & Ch. 8; Keysight/Tektronix application notes on spectrum-analyzer settings
