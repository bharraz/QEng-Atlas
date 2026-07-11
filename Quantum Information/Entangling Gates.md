#quantum-info

**An entangling gate is any two-qubit unitary that cannot be written as $U_1\otimes U_2$ and maps some product state to a non-product state** — it makes one qubit's evolution conditional on the other. One such gate plus arbitrary single-qubit rotations is universal.

# Reference

$$
\mathrm{CNOT} = \begin{pmatrix}1&0&0&0\\0&1&0&0\\0&0&0&1\\0&0&1&0\end{pmatrix}, \qquad \mathrm{CZ} = \mathrm{diag}(1,1,1,-1)
$$

CNOT flips the target iff control is $|1\rangle$; CZ phases $|11\rangle$. **Equivalent up to local Hadamards**: $\mathrm{CNOT} = (\mathbb{1}\otimes H)\,\mathrm{CZ}\,(\mathbb{1}\otimes H)$. CZ is symmetric — no control/target distinction — which often matches hardware better.

**What makes a gate entangling**: nonzero nonlocal content in the Cartan decomposition $U = (u_1\otimes u_2)\, e^{i(c_x XX + c_y YY + c_z ZZ)}\,(u_3\otimes u_4)$. CNOT, CZ, and the Mølmer-Sørensen gate $e^{-i\frac\pi4 XX}$ all sit at $c_x = \pi/4$ — maximally entangling, interconvertible by local rotations.

**Native vs compiled**: hardware gives you MS (ions) or CZ (superconducting); a textbook CNOT is compiled as native gate + single-qubit dressing. Count *native* two-qubit gates when budgeting fidelity — they're 10–100× worse than single-qubit gates on every platform.

> [!question]- Is SWAP entangling?
> No — SWAP maps every product state to a product state. But it's not local either ($\ne U_1\otimes U_2$), and it costs 3 CNOTs. "Not a local gate" and "entangling" are different properties.

# Connections

- [[Molmer-Sorensen Gate]] — the trapped-ion native entangler, via a geometric phase-space loop
- [[Bell States]] — what H + one entangling gate produces from $|00\rangle$
- [[Universal Gate Sets]] — one entangler + SU(2) = everything
- [[Single-Qubit Gates]] — the local dressing that interconverts entanglers

---
Source: Nielsen & Chuang, §4.3
