#quantum-info

**One copy of an unknown quantum state reveals almost nothing, but many identically prepared copies, measured in enough different bases, determine its density matrix: for qubits, the expectation value of every Pauli string.** The number of settings and of repetitions grows exponentially with the number of qubits.

# Reference

One qubit: three settings and you're done —

$$
\rho = \tfrac12\left( \mathbb{1} + \langle X\rangle X + \langle Y\rangle Y + \langle Z\rangle Z \right)
$$

- $\langle X\rangle, \langle Y\rangle, \langle Z\rangle$ — measured Pauli expectation values: the Bloch vector

$n$ qubits: $4^n - 1$ Pauli-string expectations ($3^n$ measurement settings), each needing enough shots for its own error bar — exponential in settings *and* copies. Practical ceiling ~8–10 qubits.

**Picture:** tomography reconstructs an object from views taken from different directions — each measurement basis is one view, and enough views fix the object.

**Linear inversion returns unphysical states**: finite-shot noise on a near-pure state pushes the estimate outside the PSD cone — negative eigenvalues, then meaningless quantities downstream (negative "entanglement", $F > 1$). Fix: **maximum likelihood estimation** constrained to $\rho \ge 0$, $\mathrm{Tr}\rho = 1$.

**MLE's boundary bias**: it piles probability on the boundary — rank-deficient estimates with zero eigenvalues and biased fidelities near pure states. Report with bootstrap error bars, and remember zero eigenvalue ≠ zero with confidence.

**SPAM sensitivity**: tomography trusts your measurement calibration completely; readout errors imprint directly on $\hat\rho$ (contrast RB, which is insensitive to them). Shot noise per expectation is binomial — budget shots accordingly.

**When full tomography is too expensive** — usually the case beyond a few qubits:

| Method | Measures | Cost |
|---|---|---|
| direct fidelity estimation | fidelity with a known target, sampling only the target's large Pauli components | scales with the target's structure, not $4^n$ |
| parity oscillations | fidelity of Bell and GHZ states ([[State and Gate Fidelity]]) | a few settings |
| entanglement witnesses | a yes/no certificate of entanglement | one or a few observables |
| classical shadows | many few-body observables from random-basis snapshots | logarithmic in the number of observables ([[Benchmarking and Characterization]]) |
| matrix-product-state tomography | states with low entanglement ([[Tensor Networks and MPS]]) | polynomial in $n$ |
| compressed sensing | nearly pure (low-rank) states | fewer settings than full tomography |

> [!question]- Why does linear inversion go unphysical exactly when the state is good (near-pure)?
> A pure state sits *on* the boundary of the PSD cone — its smallest eigenvalues are 0. Unbiased noise on the measured expectations scatters the estimate symmetrically, so ~half the time it lands outside. Mixed states sit in the interior with room to absorb the noise.

# Connections

- [[Density Matrix]] — the object being reconstructed; Bloch form is the 1-qubit inversion
- [[Maximum Likelihood Estimation]] — the constrained fit that keeps $\hat\rho$ physical
- [[Quantum Process Tomography]] — this, run on a basis of channel outputs
- [[Binomial Errors in State Detection]] — the per-expectation shot-noise floor
- [[Benchmarking and Characterization]] — scalable alternatives, including classical shadows
- [[Quantum Entropies and Information]] — entropies estimated from reconstructed or sampled states

---
Source: Nielsen & Chuang, Ch. 8.4.2; H.-Y. Huang, R. Kueng & J. Preskill, "Predicting many properties of a quantum system from very few measurements," *Nature Phys.* 16, 1050 (2020)
