#quantum-info

**Simulate $e^{-iHt}$ for $H = \sum_j H_j$ of noncommuting local terms by slicing time and exponentiating terms one at a time** — each $e^{-iH_j \delta t}$ is a small circuit, and the slicing error is pure commutator.

# Reference

**First order**:

$$
e^{-iHt} \approx \left( \prod_j e^{-iH_j t/n} \right)^n, \qquad \text{error} \sim \frac{t^2}{2n} \sum_{j<k} \big\| [H_j, H_k] \big\|
$$

**Second order (Strang/symmetric)**: forward half-steps then reversed half-steps,
$$
S_2(\delta t) = \prod_j e^{-iH_j \delta t/2} \prod_{j'\ \text{rev}} e^{-iH_{j'} \delta t/2}, \qquad \text{error } O(\delta t^3) \text{ per step}
$$

Gate count to accuracy $\epsilon$: first order $\sim t^2/\epsilon$, second order $\sim t^{3/2}/\sqrt{\epsilon}$ — the symmetric step costs ~2x per slice and almost always wins. Higher-order Suzuki recursions exist; past ~4th order the prefactors eat the gains.

**Practicalities**: error is commutator-*structured*, so group mutually commuting terms (all $ZZ$'s together — one layer, no internal error) and order the rest to kill the big commutators; empirical Trotter error is routinely 10–100x below the worst-case bound. Post-Trotter methods (qubitization, LCU) get $O(\log(1/\epsilon))$ scaling but need ancilla machinery — Trotter still wins at NISQ depths.

This is the workhorse of **Hamiltonian simulation** — the original "what is a quantum computer for" (Feynman), and the $U$ inside phase estimation for chemistry.

> [!question]- Where exactly does the Trotter error come from, and when is it strictly zero?
> From $e^{A}e^{B} = e^{A + B + \frac12[A,B] + \dots}$ — the BCH tail. If all the $H_j$ commute, the product is exact at any step size; the error budget is literally a sum of commutator norms, which is why term ordering and grouping matter.

# Connections

- [[Trotter Product Formula]] — the underlying limit and its error bounds
- [[Baker-Campbell-Hausdorff]] — where the error terms come from
- [[Quantum Phase Estimation]] — consumes the Trotterized $e^{-iHt}$ as its controlled-$U$
- [[Matrix Exponential]] — the object being approximated

---
Source: Nielsen & Chuang, Ch. 4.7 (quantum simulation)
