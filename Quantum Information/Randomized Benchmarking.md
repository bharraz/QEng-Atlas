#quantum-info

**Apply a long random sequence of Clifford gates whose product is known, finish with the one gate that undoes it, and measure whether the qubits came back to where they started: every gate adds error, so the return probability decays exponentially with sequence length, and the decay rate — not the starting value — gives the average error per gate.** Because state-preparation and measurement (SPAM) errors affect only the starting value, they drop out; that immunity is the main reason RB is the standard gate benchmark.

# Reference

Protocol: apply $m$ uniformly random Cliffords + the one Clifford that inverts the product (efficient to compute — Gottesman-Knill), measure return probability, average over many random sequences:

$$
F(m) = A\, p^m + B, \qquad r = \frac{(d-1)(1-p)}{d} \;\overset{d=2}{=}\; \frac{1-p}{2}
$$

- $F(m)$ — average return probability after $m$ random Cliffords
- $m$ — sequence length (number of Cliffords)
- $p$ — decay parameter per Clifford: the fit result
- $A, B$ — constants absorbing SPAM errors
- $d$ — Hilbert-space dimension, $2^n$ for $n$ qubits
- $r$ — average error per Clifford

**Picture:** RB is like measuring a ruler's error by laying it end to end many times: the error per step is the slope of the accumulated error, not its value after one step.

**SPAM insensitivity**: preparation and readout errors land in $A$ and $B$; the physics you want is in the *base* $p$ of the exponential, extracted from how survival scales with $m$, not from any absolute value.

**Why a clean exponential at all**: averaging over random Cliffords twirls arbitrary noise into a depolarizing channel (Clifford group is a unitary 2-design) — one decay parameter survives.

**Error per Clifford is not error per gate.** A random Clifford compiles into several native gates — 1.5 two-qubit gates on average for a two-qubit Clifford, and 1.875 pulses for a single-qubit Clifford built from $\pi$ and $\pi/2$ rotations about $x$ and $y$ — so papers divide $r$ by the average count to quote an error per native gate. Check which is being quoted before comparing.

**Variants:**

| Variant | Change | What it isolates |
|---|---|---|
| interleaved RB | alternate the gate under test with random Cliffords; compare the two decay constants | that one gate's error |
| simultaneous RB | run RB on neighbouring qubits at the same time and compare with each alone | crosstalk |
| leakage RB | also record population outside the qubit subspace | leakage and return rates per gate ([[Leakage, Erasure, and Biased Noise]]) |
| purity (unitarity) RB | measure how the purity of the output decays | the incoherent part of the error, separating it from coherent error |
| direct and mirror RB | random circuits of native layers instead of full Cliffords | error of the layers a processor runs in practice ([[Benchmarking and Characterization]]) |

**Caveats**: assumes Markovian, gate-independent noise. Coherent or low-frequency-correlated errors bend the decay away from a single exponential and can make $r$ optimistic — RB gives one number, not a noise model; it also says nothing about SPAM itself ([[Quantum State Tomography (Atlas)]] characterizes that).

**What the RB plot tells you:**

| Feature | Meaning |
|---|---|
| decay rate | error per Clifford |
| starting value $A + B$ | SPAM quality |
| decay to a level other than $1/d$, or a curve that is not one exponential | leakage, drift, or gate-dependent noise |
| large spread between different random sequences of the same length | coherent errors, which depend on the particular sequence |

> [!question]- State preparation is wrong 5% of the time. Why doesn't the extracted error per gate change?
> Prep error only rescales the amplitude $A$ of $Ap^m + B$ — the same factor at every sequence length. The fit parameter $p$ only measures how survival *changes* with $m$, which only gates touch.

# Connections

- [[Clifford Group]] — supplies both the random sequences and the 2-design twirl
- [[State and Gate Fidelity]] — $r$ is $1 - F_{\text{avg}}$ for the twirled channel
- [[Quantum Process Tomography]] — the opposite trade-off: full information, SPAM-limited, not scalable
- [[Benchmarking and Characterization]] — benchmarks beyond RB, and when each assumption fails
- [[Quantum Channels]] — the twirled depolarizing channel RB measures
- [[Leakage, Erasure, and Biased Noise]] — the errors that bend an RB decay

---
Source: Preskill, Ph219 lecture notes, Ch. 3 (channels); RB protocol: Magesan et al., PRL 106, 180504 (2011); E. Knill et al., "Randomized benchmarking of quantum gates," *Phys. Rev. A* 77, 012307 (2008)
