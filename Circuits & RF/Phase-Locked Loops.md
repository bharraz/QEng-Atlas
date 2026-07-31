#circuits #electronics

**A PLL is feedback for phase: a phase detector compares a VCO against a reference, a loop filter smooths the error, and the VCO steers until the phases track — put a ÷N in the path and the VCO locks to N× the reference.**

# Reference

Loop: phase detector → loop filter → VCO → (÷N) → back. Locked: $f_\text{out} = N f_\text{ref}$; step $N$ and you have a synthesizer carrying the reference's stability. The loop gain is $K = K_d K_v F(s)/N$, with $K_d$ = phase-detector gain (V/rad), $K_v$ = VCO tuning sensitivity (rad/s per V — the datasheet's MHz/V × 2π), and $F(s)$ the filter; the $1/N$ is why high-$N$ loops are slow and why the comparison frequency, not the output frequency, sets achievable bandwidth.

**Loop bandwidth is THE design choice:**
- **Inside** the loop BW: output follows the reference — VCO noise suppressed, reference phase noise appears **multiplied by $N$ in amplitude, i.e. $+20\log_{10}N$ dB in phase-noise power** (multiplying a frequency multiplies its phase excursions by the same factor)
- **Outside:** the VCO free-runs and shows its own phase noise
→ put the crossover where the (reference × N) and free-VCO noise curves intersect. Wide loop = agile tracking, jitter cleanup from a good reference; narrow loop = flywheel that filters a noisy reference.

**Acquisition:** capture range (grabs from cold) < lock range (holds once caught). An integrator in the loop filter (type-2 loop) gives zero static phase error and recapture after frequency steps.

**Dynamics:** it's a servo — second-order with a damping choice; underdamped loops ring on every phase step. Same phase-margin rules as any feedback loop.

Beyond synthesis: clock recovery, FM demodulation (the error signal *is* frequency), coherently tracking a drifting beat note.

> [!question]- A 10 MHz → 1 GHz synthesizer (N = 100) plateaus at −100 dBc/Hz in-loop while the reference sits at −140 dBc/Hz. Consistent?
> Yes: $20\log 100 = 40$ dB — in-loop phase noise is the reference's raised by N². Cleaner close-in output needs a better reference or a smaller N (higher comparison frequency).

# Connections

- [[PID Control]] — the loop filter is a PI controller in disguise
- [[Stability and Phase Margin]] — the same crossover analysis sets loop damping
- [[Direct Digital Synthesis]] — the other synthesis route; hybrids use a DDS as fine-step reference
- [[Mixers]] — the phase detector for RF loops

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §13.13
