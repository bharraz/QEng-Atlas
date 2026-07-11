#quantum-info

**Reconstruct $\rho$ by measuring an informationally complete set of observables on many copies** — for qubits, that means every Pauli expectation value, and the copy count is where it hurts.

# Reference

One qubit: three settings and you're done —

$$
\rho = \tfrac12\left( \mathbb{1} + \langle X\rangle X + \langle Y\rangle Y + \langle Z\rangle Z \right)
$$

$n$ qubits: $4^n - 1$ Pauli-string expectations ($3^n$ measurement settings), each needing enough shots for its own error bar — exponential in settings *and* copies. Practical ceiling ~8–10 qubits.

**Linear inversion returns unphysical states**: finite-shot noise on a near-pure state pushes the estimate outside the PSD cone — negative eigenvalues, then garbage downstream (negative "entanglement", $F > 1$). Fix: **maximum likelihood estimation** constrained to $\rho \ge 0$, $\mathrm{Tr}\rho = 1$.

**MLE's own gotcha**: it piles probability on the boundary — rank-deficient estimates with zero eigenvalues and biased fidelities near pure states. Report with bootstrap error bars, and remember zero eigenvalue ≠ zero with confidence.

**SPAM sensitivity**: tomography trusts your measurement calibration completely; readout errors imprint directly on $\hat\rho$ (contrast RB, which shrugs them off). Shot noise per expectation is binomial — budget shots accordingly.

> [!question]- Why does linear inversion go unphysical exactly when the state is good (near-pure)?
> A pure state sits *on* the boundary of the PSD cone — its smallest eigenvalues are 0. Unbiased noise on the measured expectations scatters the estimate symmetrically, so ~half the time it lands outside. Mixed states sit in the interior with room to absorb the noise.

# Connections

- [[Density Matrix]] — the object being reconstructed; Bloch form is the 1-qubit inversion
- [[Maximum Likelihood Estimation]] — the constrained fit that keeps $\hat\rho$ physical
- [[Quantum Process Tomography]] — this, run on a basis of channel outputs
- [[Binomial Errors in State Detection]] — the per-expectation shot-noise floor

---
Source: Nielsen & Chuang, Ch. 8.4.2
