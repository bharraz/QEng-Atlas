#circuits #electronics

**A comparator is an op-amp-shaped part with no feedback manners: built to slam between rails fast, not to be linear — and any comparator watching a noisy signal near threshold will chatter unless you give it hysteresis.**

# Reference

**Comparator ≠ op-amp:**
- Op-amp as comparator: internal compensation makes it slow, and recovery from saturation costs ~µs; output isn't logic-compatible. Tolerable below ~kHz, regrettable above.
- Comparator as amplifier: no compensation → oscillates with negative feedback. Don't.

**Chatter:** near threshold, noise crosses the trip point many times during one slow transit → a burst of edges. Downstream counters/interrupts see dozens of events per real one.

**Schmitt trigger fix — positive feedback makes two thresholds:** output high raises the trip point, output low lowers it; the gap must exceed the peak-to-peak noise. Feedback from output through $R_2$ to the (+) input with source resistance $R_1$:
$$
V_\text{hyst} = V_\text{swing}\,\frac{R_1}{R_1+R_2}
$$
Rule of thumb: 10–100 mV handles most lab noise; a small RC ahead of the input helps when the noise is RF.

Also: many comparators are open-collector — **no pull-up, no output** (bug #1); and slow ramps through threshold invite oscillation via stray feedback even with clean signals — hysteresis fixes that too.

> [!question]- A photodiode threshold detector fires 5–50 counts per single optical pulse. What's happening, and what's the fix?
> Chatter: noise re-crosses the single threshold during the pulse's slow edges. Add hysteresis wider than the noise ($V_\text{swing}R_1/(R_1+R_2)$), plus a small RC if the noise is RF.

# Connections

- [[Op-Amp Golden Rules and Real Limits]] — why the two parts are not interchangeable
- [[Stability and Phase Margin]] — hysteresis is positive feedback used on purpose
- [[Noise Coupling Mechanisms]] — where the threshold-crossing noise got in

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §4.3.2
