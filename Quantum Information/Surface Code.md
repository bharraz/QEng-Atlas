#quantum-info

**A logical qubit stored in a 2D grid of physical qubits, checked by 4-body local stabilizers — the code that won because its checks are nearest-neighbor and its threshold is ~1%**, within reach of real gates.

# Reference

Square lattice; two interleaved check types measured every cycle via ancillas: **plaquette** ($Z^{\otimes 4}$) and **star/vertex** ($X^{\otimes 4}$). A physical error creates a *pair* of flipped checks at the ends of an error chain; the decoder (minimum-weight perfect matching) pairs up the observed endpoints and infers the most likely chains.

**Distance and scaling**: lattice size $d$ → corrects $\lfloor(d-1)/2\rfloor$ errors; below threshold the logical error rate is exponentially suppressed:

$$
p_L \sim \left( \frac{p}{p_{\text{th}}} \right)^{\lceil d/2 \rceil}, \qquad p_{\text{th}} \approx 1\% \ \text{(circuit-level)}
$$

Rough budget: $p = 10^{-3}$, target $p_L = 10^{-12}$ → $d \approx 25$ → $\sim\!10^3$ physical qubits per logical ($\sim 2d^2$ including ancillas). Logical operators are chains of $X$ or $Z$ spanning the lattice — that's *why* small errors can't cause them.

**Why it won**: only nearest-neighbor 4-body checks in 2D (fabricable), highest practical threshold, tolerant of measurement errors (repeat syndromes in time — decoding is matching in 3D spacetime). **What it costs**: terrible encoding rate (1 logical per $\sim 2d^2$ physical), Cliffords via lattice surgery, and no transversal $T$ — non-Clifford gates need magic state distillation, which dominates the floor plan.

> [!question]- Bigger $d$ means more qubits and more places to fail — why does the logical error still fall?
> A logical failure needs an error *chain* of length $\sim d/2$ to go undetected/misdecoded; the probability of such a chain falls like $p^{d/2}$ while the number of candidate chains grows only geometrically. Below $p_{\text{th}}$ the suppression wins; above it, the entropy of chains wins and more qubits make things worse.

# Connections

- [[Quantum Error Correction]] — the general machinery this code instantiates
- [[Stabilizer Formalism]] — plaquette/star checks are stabilizer generators
- [[Magic and Nonstabilizerness]] — the missing $T$ gate and the distillation bill

---
Source: Preskill, Ph219 lecture notes, topological codes chapter
