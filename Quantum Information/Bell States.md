#quantum-info

**The four maximally entangled two-qubit states — the orthonormal basis in which entanglement is the unit of currency.** Each one's reduced single-qubit state is $\mathbb{1}/2$: all the information is in correlations, none is local.

# Reference

$$
|\Phi^\pm\rangle = \frac{|00\rangle \pm |11\rangle}{\sqrt2}, \qquad
|\Psi^\pm\rangle = \frac{|01\rangle \pm |10\rangle}{\sqrt2}
$$

**Make**: $H$ on the first qubit, then CNOT — maps computational basis $|ij\rangle$ one-to-one onto the Bell basis. **Measure**: run it backwards (CNOT, then $H$, then measure both) — this is the Bell measurement inside teleportation and dense coding.

**Local Paulis interconvert them**: $(\mathbb{1}\otimes\sigma_k)|\Phi^+\rangle$ reaches all four — one shared pair plus local ops spans the basis, which is exactly why 2 classical bits suffice in teleportation.

**CHSH**: local hidden variables bound the correlation combination at 2; Bell states reach $2\sqrt2$ (Tsirelson bound) — entanglement is experimentally distinguishable from any classical correlation.

One Bell pair = **1 ebit**, the resource unit: teleportation spends 1 ebit + 2 cbits per qubit; dense coding spends 1 ebit to send 2 cbits in 1 qubit.

> [!question]- Alice measures her half of $|\Phi^+\rangle$ — why can't Bob detect that anything happened?
> Bob's marginal is $\mathbb{1}/2$ before *and* after, whatever basis Alice picks. Correlations only become visible when the classical outcomes are compared — no signalling.

# Connections

- [[Entangling Gates]] — H+CNOT is the minimal circuit that builds them
- [[Entanglement Measures]] — Bell states saturate them: exactly 1 ebit of entropy
- [[Quantum Teleportation]] — the protocol that spends them
- [[Density Matrix]] — the $\mathbb{1}/2$ marginal is partial trace in action

---
Source: Nielsen & Chuang, Ch. 1.3.6, 2.6 (CHSH)
