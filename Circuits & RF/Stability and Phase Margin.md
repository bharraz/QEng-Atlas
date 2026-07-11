#circuits #electronics

**A feedback loop oscillates when the signal returns with gain ≥ 1 and 180° of extra phase (negative feedback turned positive); phase margin is how far from that cliff you sit at the frequency where loop gain crosses unity.**

# Reference

Read the **loop gain** Bode plot ($|GH|$, phase):
- **Phase margin** = 180° − |phase lag| at the unity-gain crossover
- **Gain margin** = dB below unity where the phase reaches −180°

| PM | closed-loop behavior |
|---|---|
| 60° | clean, ~10% overshoot — design target |
| 45° | ringy but workable |
| 30° | peaking, long ringdown |
| ≤ 0° | congratulations, an oscillator |

**Rules of thumb:**
- Cross unity on a −20 dB/dec slope; **two poles well below crossover = guaranteed trouble** (−180° arrives before gain drops).
- **Adding gain can destabilize:** more gain pushes the crossover to higher frequency where more poles have piled up phase. That's why the lock oscillates when you crank it.
- Closed-loop ringing frequency ≈ crossover frequency — read it off the scope and you know *where* in the loop to fix phase.
- Hidden phase: pure delay contributes $-\omega\tau$, linear in f — cables, digital latency, acoustic transit in an AOM all eat margin as you push bandwidth.

> [!question]- The lock is stable at low gain, oscillates at ~30 kHz when raised. What does 30 kHz tell you, and name two fixes that aren't "less gain."
> 30 kHz is the unity-gain crossover where the margin ran out. Add phase lead there (D term / lead network), or remove lag below it (shorter delay, move a filter pole up) — reshape the loop instead of retreating.

# Connections

- [[Transfer Functions and Bode Plots]] — the plot this analysis is performed on
- [[PID Control]] — the knobs that reshape loop gain and phase
- [[Op-Amp Golden Rules and Real Limits]] — internal compensation is this problem pre-solved (until you load it capacitively)
- [[Driven Damped Harmonic Oscillator]] — low phase margin ↔ an underdamped closed-loop pole pair

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §4.9
