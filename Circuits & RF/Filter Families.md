#circuits #electronics

**A filter of a given order can be designed for a flat passband, a steep cutoff, or a clean step response, but not all at once; each named family maximizes one at the others' expense.** Pick by what you're protecting: amplitude accuracy, rejection, or pulse shape.

# Reference

| Family | Passband | Rolloff near cutoff | Step response | Use when |
|---|---|---|---|---|
| **Butterworth** | maximally flat | moderate | some overshoot | default; amplitude accuracy |
| **Chebyshev** | ripple (spec'd dB) | steep | ringy | rejection per pole matters |
| **Bessel** | droopy | slow | **clean — linear phase, flat group delay** | pulses, timing, anything you'll view on a scope |
| **Elliptic** | ripple both bands | steepest (stopband zeros) | worst ringing | brick-wall/anti-alias needs |

**Picture:** a fixed number of poles placed in the complex plane: on a circle for a flat passband (Butterworth), pushed toward the imaginary axis for steepness at the cost of ringing (Chebyshev), arranged for constant delay for clean pulses (Bessel).

Far from cutoff every $n$-pole filter falls at $-20n$ dB/dec — the families differ in the octave *around* $f_c$, which is where you live.

**Group delay is the often-overlooked spec:** constant delay = all frequencies arrive together = undistorted waveform. Chebyshev/elliptic delay peaks near cutoff, so a filtered square pulse rings for many cycles. **Filtering a pulse? Bessel.**

Order budget: each pole adds 6 dB/octave; needing 40 dB one octave out means ~7 poles of Butterworth, ~5 of Chebyshev — or rethinking the corner placement.

> [!question]- Your anti-ringing instinct says Bessel, your rejection spec says elliptic. What's the standard escape?
> Move the corner up: a higher-order Bessel/Butterworth with $f_c$ pushed out gives clean time response *and* adequate rejection — or filter digitally afterward with zero-phase filtfilt. Steepness right at the corner is only mandatory when bandwidth is genuinely scarce.

# Connections

- [[RC and RL Filters]] — the single-pole building block
- [[Sallen-Key Topology]] — how these get built, two poles per op-amp
- [[Digital Filters]] — linear-phase FIR gives Bessel-like behavior with brick walls
- [[Transfer Functions and Bode Plots]] — the language the families are specified in
- [[Filtering Power and Signal Lines]] — passive filtering of supply, bias, and signal lines

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §6.2
