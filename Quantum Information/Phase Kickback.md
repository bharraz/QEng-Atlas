#quantum-info

**Apply a controlled-$U$ to an eigenstate and the phase lands on the *control*** — the target is unchanged (it's an eigenstate!), so the eigenvalue phase, global on that branch, becomes a relative phase of the control's superposition.

# Reference

$U|u\rangle = e^{i\theta}|u\rangle$:

$$
\frac{|0\rangle + |1\rangle}{\sqrt2}\,|u\rangle \;\xrightarrow{\text{c-}U}\; \frac{|0\rangle + e^{i\theta}|1\rangle}{\sqrt2}\,|u\rangle
$$

Target untouched, control rotated — information flows *backwards* through the controlled gate. Control/target labels are basis fictions anyway: CZ is symmetric, and CNOT in the $X$ basis flips the roles.

**The oracle trick** (Deutsch-Jozsa, Grover): put the ancilla in $|-\rangle$; then $|x\rangle|-\rangle \to (-1)^{f(x)}|x\rangle|-\rangle$ — a bit-flip oracle becomes a *phase* oracle, imprinting $f$ onto the query register where interference can act on it. The ancilla is never consumed.

**The QPE engine**: controlled-$U^{2^k}$ kicks $e^{2\pi i \varphi 2^k}$ onto ancilla $k$ — binary digits of the eigenphase, delivered one qubit at a time and decoded by the inverse QFT.

CNOT worked in the $X$ basis: $|{-}\rangle$ is the $-1$ eigenstate of $X$, so CNOT (a controlled-$X$) gives $|x\rangle|-\rangle \to (-1)^x |x\rangle|-\rangle$ — i.e. a $Z$ on the "control". Same gate, opposite arrow.

> [!question]- The oracle computes $f$ into the ancilla — how does the ancilla end up unentangled and the register changed?
> Because $|-\rangle$ is an eigenstate of the XOR action: $|-\oplus f(x)\rangle = (-1)^{f(x)}|-\rangle$. The would-be record factors out as a phase on the register branch — no which-value information stays in the ancilla, so no entanglement, just interference-ready phases.

# Connections

- [[Quantum Phase Estimation]] — kickback run in parallel across a register
- [[Entangling Gates]] — controlled operations, whose direction of action is basis-dependent
- [[Canonical Quantum Algorithms]] — the phase-oracle construction under DJ and Grover

---
Source: Nielsen & Chuang, Ch. 1.4.3–1.4.4
