#circuits #electronics

**A phase-locked loop (PLL) is feedback for phase: it makes a tunable oscillator follow a stable reference. A phase detector compares a voltage-controlled oscillator (VCO, whose frequency is set by a control voltage) against the reference, a loop filter smooths the error, and the VCO steers until the phases track — put a frequency divider (÷N, one output cycle per N input cycles) in the path and the VCO locks to N× the reference.**

# Reference

Loop: phase detector → loop filter → VCO → (÷N) → back. Locked: $f_\text{out} = N f_\text{ref}$; step $N$ and you have a synthesizer carrying the reference's stability. The loop gain is $K = K_d K_v F(s)/N$:

- $K_d$ — phase-detector gain (V/rad)
- $K_v$ — VCO tuning sensitivity (rad/s per V — the datasheet's MHz/V × 2π)
- $F(s)$ — the loop filter's transfer function
- $N$ — the divider ratio

The $1/N$ is why high-$N$ loops are slow, and why the comparison frequency (the frequency at the phase detector, $f_\text{ref}$), not the output frequency, sets achievable bandwidth.

**Picture:** two runners on a circular track: the follower adjusts its speed to hold a fixed distance behind the leader, and with a divider it runs $N$ laps for each lap of the leader.

**Loop bandwidth is the main design choice:**
- **Inside** the loop bandwidth: output follows the reference — VCO noise suppressed, reference phase noise appears **multiplied by $N$ in amplitude, i.e. $+20\log_{10}N$ dB in phase-noise power** (multiplying a frequency multiplies its phase excursions by the same factor)
- **Outside:** the VCO free-runs and shows its own phase noise
→ put the crossover where the (reference × N) and free-VCO noise curves intersect. Wide loop = agile tracking, jitter cleanup from a good reference; narrow loop = flywheel that filters a noisy reference.

Phase noise is quoted in dBc/Hz: power in a 1 Hz band at a given offset, in dB relative to the carrier.

**Acquisition:** capture range (the offset from which the loop can grab lock starting unlocked, "from cold") < lock range (the offset it holds once caught). An integrator in the loop filter makes a type-2 loop — two integrations around the loop, since the VCO already integrates frequency into phase — which gives zero static phase error and recapture after frequency steps.

**Dynamics:** it's a servo — second-order with a damping choice; underdamped loops ring on every phase step. Same phase-margin rules as any feedback loop.

Beyond synthesis: clock recovery, FM (frequency-modulation) demodulation (the error signal *is* frequency), coherently tracking a drifting beat note.

> [!question]- A 10 MHz → 1 GHz synthesizer (N = 100) plateaus at −100 dBc/Hz in-loop while the reference sits at −140 dBc/Hz. Consistent?
> Yes: $20\log 100 = 40$ dB — in-loop phase noise is the reference's raised by N². Cleaner close-in output needs a better reference or a smaller N (higher comparison frequency).

# Connections

- [[PID Control]] — the loop filter is a PI controller
- [[Stability and Phase Margin]] — the same crossover analysis sets loop damping
- [[Direct Digital Synthesis]] — the other synthesis route; hybrids use a DDS as fine-step reference
- [[Mixers]] — the phase detector for RF loops
- [[Fiber Noise Cancellation]] — a PLL that locks an optical beat to an RF reference

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §13.13
