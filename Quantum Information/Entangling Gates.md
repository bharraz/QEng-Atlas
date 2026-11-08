#quantum-info

**Two qubits that interact — through a shared vibrational mode, a blockaded Rydberg excitation, or a coupling between two circuits — evolve under a unitary that depends on both of their states at once; when that unitary turns some product state into an entangled one, it is an entangling gate.** One such gate plus arbitrary single-qubit rotations is universal.

# Reference

$$
\mathrm{CNOT} = \begin{pmatrix}1&0&0&0\\0&1&0&0\\0&0&0&1\\0&0&1&0\end{pmatrix}, \qquad \mathrm{CZ} = \mathrm{diag}(1,1,1,-1)
$$

CNOT flips the second qubit (the target) iff the first (the control) is $|1\rangle$; CZ phases $|11\rangle$. **Equivalent up to local Hadamards**: $\mathrm{CNOT} = (\mathbb{1}\otimes H)\,\mathrm{CZ}\,(\mathbb{1}\otimes H)$. CZ is symmetric — no control/target distinction — which often matches hardware better.

**What makes a gate entangling**: nonzero nonlocal content in the Cartan decomposition

$$
U = (u_1\otimes u_2)\, e^{i(c_x XX + c_y YY + c_z ZZ)}\,(u_3\otimes u_4)
$$

- $u_1, \dots, u_4$ — single-qubit unitaries: local dressing, free to change
- $c_x, c_y, c_z$ — nonlocal coordinates (rad): what no local operation alters

Two gates with the same $(c_x, c_y, c_z)$ are interconvertible by single-qubit rotations, so the coordinates name a gate's entangling content:

| Gate | $(c_x, c_y, c_z)$ | Where it appears |
|---|---|---|
| CNOT, CZ, Mølmer–Sørensen $e^{-i\frac\pi4 XX}$ | $(\pi/4, 0, 0)$ | ions (MS), neutral atoms and superconducting circuits (CZ) |
| controlled phase CPHASE($\varphi$) | $(\varphi/4, 0, 0)$ | Rydberg and superconducting gates with a tunable conditional phase; part of fSim |
| iSWAP | $(\pi/4, \pi/4, 0)$ | superconducting circuits with exchange coupling |
| $\sqrt{\mathrm{iSWAP}}$ | $(\pi/8, \pi/8, 0)$ | same |
| $\sqrt{\mathrm{SWAP}}$ | $(\pi/8, \pi/8, \pi/8)$ | spins with exchange coupling ([[Exchange Interactions]]) |
| SWAP | $(\pi/4, \pi/4, \pi/4)$ | not entangling (question below) |

**Picture:** an entangling gate is a conditional phase: each qubit's phase advances by an amount that depends on the other's state, and the gate is the time during which that rule is switched on.

**Native vs compiled**: hardware gives you MS (ions) or CZ (superconducting); a textbook CNOT is compiled as native gate + single-qubit dressing. Any two-qubit unitary needs at most three CNOT-class gates; SWAP needs exactly three, and a CNOT needs two iSWAPs. Count *native* two-qubit gates when budgeting fidelity — they're 10–100× worse than single-qubit gates on every platform. How each platform produces its native gate is on [[Two-Qubit Gate Mechanisms]].

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| Ramsey on the target with the control in $\lvert 0\rangle$, then in $\lvert 1\rangle$ | the conditional phase, i.e. the CPHASE angle |
| populations and parity oscillations of the Bell state the gate makes | Bell-state fidelity ([[State and Gate Fidelity]]) |
| interleaved randomized benchmarking | the gate's average error ([[Randomized Benchmarking]]) |
| process tomography | the full error map, including which nonlocal coordinate is off ([[Quantum Process Tomography]]) |

> [!question]- Is SWAP entangling?
> No — SWAP maps every product state to a product state. But it's not local either ($\ne U_1\otimes U_2$), and it costs 3 CNOTs. "Not a local gate" and "entangling" are different properties.

# Connections

- [[Molmer-Sorensen Gate]] — the trapped-ion native entangler, via a geometric phase-space loop
- [[Bell States]] — what H + one entangling gate produces from $|00\rangle$
- [[Universal Gate Sets]] — one entangler + SU(2) = everything
- [[Single-Qubit Gates]] — the local dressing that interconverts entanglers
- [[Two-Qubit Gate Mechanisms]] — the physical interaction behind each platform's native gate
- [[Qudits and Multi-Qubit Gates]] — gates acting on more than two qubits at once

---
Source: Nielsen & Chuang, §4.3; B. Kraus & J. I. Cirac, "Optimal creation of entanglement using a two-qubit gate," *Phys. Rev. A* 63, 062309 (2001)
