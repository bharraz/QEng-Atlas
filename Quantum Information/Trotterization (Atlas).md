#quantum-info

**A quantum computer can apply each piece of a Hamiltonian $H = \sum_j H_j$ as its own short circuit, $e^{-iH_j\delta t}$, but not the full evolution at once; slicing time into steps and applying the pieces in turn reproduces $e^{-iHt}$ up to an error made only of the pieces' commutators, which shrinks as the steps get shorter.**

# Reference

**First order**:

$$
e^{-iHt} \approx \left( \prod_j e^{-iH_j t/n} \right)^n, \qquad \text{error} \sim \frac{t^2}{2n} \sum_{j<k} \big\| [H_j, H_k] \big\|
$$

- $H_j$ — the individual terms, each easy to exponentiate
- $t$ — total simulated time (s, or in units of $\hbar/\lVert H\rVert$)
- $n$ — number of Trotter steps, so $\delta t = t/n$
- $\lVert[H_j, H_k]\rVert$ — size of the commutator: the source of all the error

**Second order (Strang/symmetric)**: forward half-steps then reversed half-steps,
$$
S_2(\delta t) = \prod_j e^{-iH_j \delta t/2} \prod_{j'\ \text{rev}} e^{-iH_{j'} \delta t/2}, \qquad \text{error } O(\delta t^3) \text{ per step}
$$

Gate count to accuracy $\epsilon$: first order $\sim t^2/\epsilon$, second order $\sim t^{3/2}/\sqrt{\epsilon}$ — the symmetric step costs ~2x per slice and is almost always the better choice. Higher-order Suzuki recursions exist; past ~4th order the growing prefactors outweigh the gains.

**Picture:** walking a diagonal by alternating steps east and north: short steps stay close to the diagonal, and the deviation exists only because the two directions do not commute.

**Practicalities**: error is commutator-*structured*, so group mutually commuting terms (all $ZZ$'s together — one layer, no internal error) and order the rest to minimize the large commutators; empirical Trotter error is routinely 10–100x below the worst-case bound. Post-Trotter methods (qubitization, LCU) get $O(\log(1/\epsilon))$ scaling but need ancilla machinery — Trotter is still preferred at NISQ depths.

**On real hardware there is an optimum step count:** more steps reduce the Trotter error but add gates, and each gate adds its own error, so the simulation fidelity rises and then falls as the number of steps grows. Experiments plot that curve to choose the step size.

| Approach | How the Hamiltonian is applied | Error |
|---|---|---|
| digital (Trotterized) | gates approximating each term | Trotter error plus gate errors, both quantifiable |
| analog | the hardware's native Hamiltonian runs continuously ([[Analog Quantum Simulation]]) | uncorrected calibration and decoherence errors |
| digital–analog | native interactions as the entangling layer, single-qubit gates in between | a mix of both |

This is the standard method of **Hamiltonian simulation** — the original "what is a quantum computer for" (Feynman), and the $U$ inside phase estimation for chemistry.

> [!question]- Where exactly does the Trotter error come from, and when is it strictly zero?
> From $e^{A}e^{B} = e^{A + B + \frac12[A,B] + \dots}$ — the BCH tail. If all the $H_j$ commute, the product is exact at any step size; the error budget is a sum of commutator norms, which is why term ordering and grouping matter.

# Connections

- [[Trotter Product Formula]] — the underlying limit and its error bounds
- [[Baker-Campbell-Hausdorff]] — where the error terms come from
- [[Quantum Phase Estimation]] — consumes the Trotterized $e^{-iHt}$ as its controlled-$U$
- [[Matrix Exponential]] — the object being approximated
- [[Analog Quantum Simulation]] — running the Hamiltonian natively instead of by gates
- [[Quench Dynamics and Thermalization]] — the many-body dynamics these simulations usually target
- [[Variational Quantum Algorithms]] — QAOA layers as Trotter steps whose angles are optimized

---
Source: Nielsen & Chuang, Ch. 4.7 (quantum simulation); A. M. Childs, Y. Su, M. C. Tran, N. Wiebe & S. Zhu, "Theory of Trotter error with commutator scaling," *Phys. Rev. X* 11, 011020 (2021)
