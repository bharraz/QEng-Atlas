#quantum-optics

**A field is a collection of modes, each mode is a harmonic oscillator, and "particle number" is just the mode's excitation level.** Identical particles force this: labeled-particle wavefunctions carry $N!$ redundant terms, and processes that change $N$ (emission, absorption) can't even be written in first quantization.

# Reference

Occupation-number basis $|n_1, n_2, \ldots\rangle$ — the state is fully specified by how many quanta sit in each mode. Per mode:

$$
a_k^\dagger|n_k\rangle = \sqrt{n_k+1}\,|n_k+1\rangle, \qquad a_k|n_k\rangle = \sqrt{n_k}\,|n_k-1\rangle, \qquad [a_k, a_{k'}^\dagger] = \delta_{kk'}
$$

**Fermions swap commutators for anticommutators:** $\{c_k, c_{k'}^\dagger\} = \delta_{kk'}$, so $(c^\dagger)^2 = 0$ and $n_k \in \{0,1\}$ — Pauli exclusion is the algebra, not an extra postulate.

**Field operators are mode sums:** $\hat\psi(\mathbf r) = \sum_k u_k(\mathbf r)\, a_k$ annihilates a particle at $\mathbf r$; "amplitude at a point" and "quanta per mode" are two bases for the same Fock space. Free Hamiltonians become bookkeeping: $H = \sum_k \hbar\omega_k\, a_k^\dagger a_k$, interactions are polynomials in $a, a^\dagger$.

**Why it's forced, not a convenience:** hand-symmetrizing $N$ bosons costs $N!$ terms carrying zero extra information, and the occupation representation stores the same state as one ket. Anything that creates or destroys quanta lives natively here.

> [!question]- Why can't first quantization describe spontaneous emission?
> A fixed-$N$ Hilbert space has no operator connecting $N$ to $N \pm 1$ particles. Fock space stacks all the number sectors, and $a^\dagger$ moves between them — emission is literally $\sigma_- a_k^\dagger$.

# Connections

- [[Ladder Operators]] — the same $[a, a^\dagger]=1$ machine, one copy per mode
- [[Field Quantization of Light]] — the EM field run through this construction: photons as mode excitations
- [[Fock States]] — the occupation-number basis states of a single mode
- [[Quantum Harmonic Oscillator]] — what each mode individually is

---
Source: Fetter & Walecka, *Quantum Theory of Many-Particle Systems*, Ch. 1
