#quantum-info

**Lay physical qubits on a square grid, alternate data qubits with measurement qubits, and repeatedly measure the product of four $Z$s or four $X$s around each small square: an error on a data qubit flips the checks next to it, and the logical qubit lives in correlations that only an error chain stretching across the grid can change.** Its checks are nearest-neighbour and its threshold is about 1%, which is why it is the leading choice for hardware.

# Reference

Square lattice; two interleaved check types measured every cycle via ancillas: **plaquette** ($Z^{\otimes 4}$) and **star/vertex** ($X^{\otimes 4}$). A physical error creates a *pair* of flipped checks at the ends of an error chain; the decoder (minimum-weight perfect matching) pairs up the observed endpoints and infers the most likely chains. In the common rotated layout a distance-$d$ patch uses $d^2$ data qubits and $d^2 - 1$ measurement qubits.

**Picture:** errors are strings on a sheet. The checks see only a string's endpoints; the decoder joins endpoints back up; a logical error is a string that crosses the sheet from one edge to the opposite one, which has no endpoints to see.

**Distance and scaling**: lattice size $d$ → corrects $\lfloor(d-1)/2\rfloor$ errors; below threshold the logical error rate is exponentially suppressed:

$$
p_L \sim \left( \frac{p}{p_{\text{th}}} \right)^{\lceil d/2 \rceil}, \qquad p_{\text{th}} \approx 1\% \ \text{(circuit-level)}
$$

- $p$ — physical error probability per gate/cycle (dimensionless)
- $p_{\text{th}}$ — threshold, the value of $p$ at which the code stops helping
- $d$ — code distance, the lattice linear size in qubits: length of the shortest undetectable error chain
- $p_L$ — logical error probability per cycle

The exponent $\lceil d/2\rceil$ is the number of physical errors needed to reach halfway across the lattice — hence the suppression is *exponential in $d$* but only when the base $p/p_{\text{th}} < 1$. Two consequences: below threshold, each increase in distance lowers the logical error rate by a constant factor; above it, the same equation runs backwards and more qubits are worse.

Rough budget: $p = 10^{-3}$, target $p_L = 10^{-12}$ → $d \approx 25$ → $\sim\!10^3$ physical qubits per logical ($\sim 2d^2$ including ancillas). Logical operators are chains of $X$ or $Z$ spanning the lattice — that's *why* small errors can't cause them.

**One round of the cycle:**

1. Reset the measurement qubits.
2. Entangle each with its four data neighbours by four two-qubit gates. Their order is chosen so that a fault on a measurement qubit spreads to data qubits along a direction that does not shorten the logical chain.
3. Measure the measurement qubits; compare with the previous round to get detection events ([[Quantum Error Correction (Atlas)]]).
4. Repeat. Decoding works on the space–time pattern of detection events, which is why measurement errors are tolerated.

**Why it is widely adopted**: only nearest-neighbor 4-body checks in 2D (fabricable), a high threshold among codes with local checks, tolerant of measurement errors (repeat syndromes in time — decoding is matching in 3D spacetime). **What it costs**: very low encoding rate (1 logical per $\sim 2d^2$ physical), Cliffords via lattice surgery, and no transversal $T$ — non-Clifford gates need magic state distillation, which dominates the floor plan.

**Logical operations by lattice surgery:** two patches are merged by measuring joint checks along their shared boundary, which measures a logical $X\otimes X$ or $Z\otimes Z$; splitting them again completes the operation. Sequences of such joint measurements, with single-patch operations, give a logical CNOT without any transversal gate ([[Mid-Circuit Measurement and Feedforward]]).

**What below-threshold experiments plot:**

| Plot | What it shows |
|---|---|
| logical error per round for $d = 3, 5, 7$ | suppression factor $\Lambda$ from the ratio between successive distances |
| detection-event probability per round, per stabilizer | uniformity of the physical errors; hot spots and drift |
| repetition-code runs at large distance | the floor set by rare correlated events, visible once ordinary errors are suppressed far enough |

> [!question]- Bigger $d$ means more qubits and more places to fail — why does the logical error still fall?
> A logical failure needs an error *chain* of length $\sim d/2$ to go undetected/misdecoded; the probability of such a chain falls like $p^{d/2}$ while the number of candidate chains grows only geometrically. Below $p_{\text{th}}$ the suppression dominates; above it, the growing number of chains dominates and more qubits make things worse.

# Connections

- [[Quantum Error Correction (Atlas)]] — the general machinery this code instantiates
- [[Stabilizer Formalism]] — plaquette/star checks are stabilizer generators
- [[Magic and Nonstabilizerness]] — the missing $T$ gate and the distillation bill
- [[Mid-Circuit Measurement and Feedforward]] — the measure-and-reset every round depends on
- [[Leakage, Erasure, and Biased Noise]] — leakage, which matching decoders do not model, and erasures, which they handle better
- [[Topological Phases of Matter]] — the surface code as a topologically ordered phase

---
Source: Preskill, Ph219 lecture notes, topological codes chapter; A. G. Fowler, M. Mariantoni, J. M. Martinis & A. N. Cleland, "Surface codes: towards practical large-scale quantum computation," *Phys. Rev. A* 86, 032324 (2012)
