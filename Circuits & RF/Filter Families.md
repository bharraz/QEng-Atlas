#circuits #electronics

**All filter families trade the same three currencies — passband flatness, cutoff steepness, and time-domain behavior — and each named family maximizes one at the others' expense.** Pick by what you're protecting: amplitude accuracy, rejection, or pulse shape.

# Reference

| Family | Passband | Rolloff near cutoff | Step response | Use when |
|---|---|---|---|---|
| **Butterworth** | maximally flat | moderate | some overshoot | default; amplitude accuracy |
| **Chebyshev** | ripple (spec'd dB) | steep | ringy | rejection per pole matters |
| **Bessel** | droopy | slow | **clean — linear phase, flat group delay** | pulses, timing, anything you'll view on a scope |
| **Elliptic** | ripple both bands | steepest (stopband zeros) | worst ringing | brick-wall/anti-alias needs |

Far from cutoff every $n$-pole filter falls at $-20n$ dB/dec — the families differ in the octave *around* $f_c$, which is where you live.

**Group delay is the sleeper spec:** constant delay = all frequencies arrive together = undistorted waveform. Chebyshev/elliptic delay peaks near cutoff, so a filtered square pulse rings for many cycles. **Filtering a pulse? Bessel.**

Order budget: each pole buys 6 dB/octave; needing 40 dB one octave out means ~7 poles of Butterworth, ~5 of Chebyshev — or rethinking the corner placement.

> [!question]- Your anti-ringing instinct says Bessel, your rejection spec says elliptic. What's the standard escape?
> Move the corner up: a higher-order Bessel/Butterworth with $f_c$ pushed out gives clean time response *and* adequate rejection — or filter digitally afterward with zero-phase filtfilt. Steepness right at the corner is only mandatory when bandwidth is genuinely scarce.

# Connections

- [[RC and RL Filters]] — the single-pole building block
- [[Sallen-Key Topology]] — how these get built, two poles per op-amp
- [[Digital Filters]] — linear-phase FIR gives Bessel-like behavior with brick walls
- [[Transfer Functions and Bode Plots]] — the language the families are specified in

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §6.2
