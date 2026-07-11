#circuits

**An IC is transistors plus interconnect fabricated as one object; digital ICs hide the transistor behind an abstraction (logic levels, clocks) that tolerates enormous device variation, while analog ICs live off the transistor's actual physics and pay for it in matching, noise, and process sensitivity.** For a physicist the working questions are: what abstraction is this chip offering, what physics leaks through it, and which datasheet numbers encode the leak.

# Reference

**The MOSFET in one paragraph.** A gate voltage capacitively controls a channel between source and drain: off below threshold $V_T$ (current falls 10× per ~70–100 mV of gate swing below $V_T$ — the *subthreshold slope*, floor set by $k_BT/e \times \ln 10 = 60$ mV/decade at 300 K), roughly a voltage-controlled current source above it. It is a *transconductance* device: $g_m = \partial I_D/\partial V_{GS}$ is the gain currency of analog design. CMOS = complementary N and P devices in series: one is always off at rest, so **static power ≈ 0 and energy is spent only on switching** — the fact that made digital scaling possible.

## Digital — the abstraction and its residue

Logic levels + noise margins mean a gate *regenerates* the signal: analog noise below the margin is erased at every stage. That's the whole trick — billions of marginal transistors compute reliably because each stage re-digitizes. What still leaks through:

- **Switching energy and heat**: $E \approx CV^2$ per node toggle; power $= \alpha C V^2 f$. Voltage is the lever (quadratic), which is why cores race to the lowest $V$ that still switches.
- **Timing, not voltage, is the analog residue.** Gates take real time; a clocked system works only if data settles before the clock edge (setup/hold windows). Violate them — or clock two unsynchronized domains together — and you get **metastability**: a flip-flop hanging between levels for an unbounded time. Any signal entering an FPGA from your apparatus asynchronously *must* go through a synchronizer chain; this is the digital failure mode experimentalists actually meet.
- **Edges are RF.** A 1 ns edge has ~GHz content regardless of the clock rate: digital lines radiate into your analog rail and demand [[Transmission Lines|termination]] once trace delay ~ rise time. Ground bounce and simultaneous-switching noise are the same physics inside the package. Treat fast digital as an RF interference source colocated with your measurement ([[Grounding and Shielding Practice]]).
- **The catalog view:** glue logic, FPGAs (see [[What an FPGA Is]]), microcontrollers, ASICs — ascending commitment; the experimentalist's spectrum is usually FPGA (deterministic ns timing, parallel) vs microcontroller (µs-ms, sequential, easy).

## Analog — the physics with no abstraction to hide behind

An op-amp datasheet is a list of the transistor physics the feedback couldn't remove ([[Op-Amp Golden Rules and Real Limits]]). The IC-specific insights:

- **Matching, not absolute accuracy.** On-die absolute values (R, C, $V_T$) vary ±20% between fabrication runs; *adjacent identical devices on one die* match to ~0.1%. All monolithic design is built from ratios and symmetric pairs (differential pairs, current mirrors, R-2R ladders) — and this is also the answer to "why is this IC's topology so baroque": it's algebra that cancels absolute values in favor of ratios. Mismatch scales as $1/\sqrt{\text{area}}$ (averaging over dopant fluctuations), so precision parts are physically large or trimmed at the factory.
- **Noise you inherit:** thermal ([[Johnson-Nyquist Noise]]) and shot noise set white floors; MOS transistors add strong [[Flicker Noise|1/f noise]] (carrier trapping at the gate-oxide interface — corner frequencies of kHz–MHz, much worse than bipolar). The standard countermeasure is **modulation past the corner**: chopper/auto-zero amplifiers ([[Lock-In Detection]] on-chip) buy µV-stable DC at the cost of switching artifacts.
- **The specs that bite in the lab:** input bias current (fA for CMOS electrometers, nA for bipolar — decides your photodiode TIA), offset drift µV/°C, CMRR/PSRR falling with frequency (your 50 Hz rejection is worse than the DC spec), rail-to-rail input stages swapping offset mid-range (crossover distortion in the pair-swap).
- **Mixed signal** — where the two worlds share a die and the digital residue lands in the analog floor: converter resolution is real only up to the effective number of bits, $\mathrm{ENOB} = (\mathrm{SINAD} - 1.76)/6.02$, and clock **jitter** caps SNR at $-20\log(2\pi f_{\text{in}}\sigma_t)$ — see [[ADC and DAC Realities]]. Separate grounds/planes, return-current discipline, and synchronous sampling are the defenses.

**Key considerations when *choosing* ICs for an experiment** (the checklist form): noise density at your signal frequency (not DC) and the 1/f corner; bandwidth × gain reserve ([[Stability and Phase Margin|phase margin]] if you add feedback); bias current vs source impedance; supply rejection at your interference frequencies; latency and its determinism (FPGA vs MCU vs analog); thermal drift over your run time; and for anything cryogenic — most silicon works cold but specs silently void: carrier freeze-out below ~40 K for bulk CMOS (SiGe and specialized CMOS survive to 4 K, the cryo-CMOS control literature for qubits lives exactly here).

> [!question]- Why can a $0.50 microcontroller contain 10⁵ transistors that all work, while a precision op-amp with ~50 transistors costs $10 and still drifts?
> The digital transistors don't have to be *good* — regeneration at every gate erases their individual variation; they only have to switch. The op-amp's input pair must be *identical* to sub-mV over temperature and time, and no feedback can remove what the input stage itself contributes: its offset, drift, and noise are referred directly to your signal. Digital buys reliability from architecture; analog must buy it from physics — large matched geometries, trimming, choppers — and that is what you're paying for.

# Connections

- [[Op-Amp Golden Rules and Real Limits]] — the analog datasheet decoded
- [[ADC and DAC Realities]] — the mixed-signal boundary in detail
- [[What an FPGA Is]] — the digital workhorse of experiment control
- [[Flicker Noise]] — the MOS 1/f burden and chopper escape
- [[Johnson-Nyquist Noise]] / [[Shot Noise]] — the white floors
- [[Transmission Lines]] / [[Grounding and Shielding Practice]] — fast edges as interference
- [[Comparators and Hysteresis]] — the one-bit bridge between the two worlds

---
Source: Horowitz & Hill, *The Art of Electronics*, Ch. 3–5, 10–12; Razavi, *Design of Analog CMOS Integrated Circuits*, Ch. 2, 7, 14
