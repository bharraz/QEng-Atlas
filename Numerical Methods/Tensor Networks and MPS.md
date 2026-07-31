#numerics #quantum-info

**A general $N$-qubit state needs $2^N$ amplitudes; a matrix product state stores $\sim N D^2$ of them, where the bond dimension $D$ counts the entanglement kept across each cut.** Ground states of local 1D Hamiltonians obey an area law — entanglement bounded independent of size — so they live exactly in this compressible corner. The compression engine is the SVD.

# Reference

**Construction.** Cut the chain between sites $k$ and $k{+}1$; Schmidt-decompose ([[Singular Value Decomposition]]):

$$|\psi\rangle = \sum_{\alpha=1}^{\chi} \lambda_\alpha\, |L_\alpha\rangle |R_\alpha\rangle, \qquad S = -\sum_\alpha \lambda_\alpha^2 \ln \lambda_\alpha^2,$$

where $\lambda_\alpha$ = Schmidt coefficients across the cut and $S$ = entanglement entropy. Keep the $D$ largest $\lambda_\alpha$ at every bond:

$$\psi_{s_1 \cdots s_N} = A^{s_1}_{[1]} A^{s_2}_{[2]} \cdots A^{s_N}_{[N]}, \qquad A^{s_k}\ \text{a}\ D \times D\ \text{matrix per local state } s_k.$$

Truncation error $= \sum_{\alpha > D} \lambda_\alpha^2$ (discarded weight) — measured, controlled, and the single convergence knob: rerun at larger $D$; if observables move, physics was being truncated.

**Where it works and where it dies** — all entanglement accounting:

| regime | $S$ scaling | required $D$ |
|---|---|---|
| gapped 1D ground state | const (area law) | const — arbitrary $N$ |
| 1D critical point | $\ln N$ | polynomial in $N$ |
| 2D (cylinder of width $L$) | $\propto L$ | $e^{L}$ — the practical ceiling |
| global quench, time $t$ | $\propto t$ | $e^{t}$ — long-time dynamics inaccessible |

The last row is where classical simulability of quantum experiments actually dies — entanglement growth, not qubit count.

**Algorithms** (ITensor, TeNPy, quimb):

- **DMRG** — variational ground-state search over MPS, sweeping site by site; each local update is a small eigenproblem ([[Exact Diagonalization and Sparse Methods|Lanczos]]). Energies to $10^{-10}$ in 1D routinely.
- **TEBD** — Trotterize $e^{-iHt}$ into local gates ([[Trotter Product Formula]]), apply, re-truncate by SVD per step. **TDVP** — project the Schrödinger equation onto the MPS manifold; better for long-range terms. Imaginary time → thermal states.
- **MPO** — operators in the same chain form; local and power-law Hamiltonians (ion-chain $J_{ij} \propto 1/r^\alpha$) compress to small MPOs.
- Beyond chains: PEPS (2D, expensive contraction), MERA (critical/scale-invariant), tensor-network contraction of circuits (the quantum-supremacy-spoofing computations).

**Glossary for the literature:** bond dimension $D$ (also $\chi$) — entanglement kept; discarded weight — the error meter; canonical form — the gauge making truncation optimal and local expectation values $O(D^3)$; entanglement spectrum — the $\lambda_\alpha$ themselves (degeneracies diagnose topological order); area vs volume law — compressible vs not.

**Versus ED:** ED is exact and structure-free to ~20 qubits; MPS reaches hundreds of sites in 1D when $S$ is low. Neither reaches deep 2D or long-time quenches — QMC (sign problem permitting) or a quantum simulator. Which side of that line an experiment sits on is the quantum-advantage question.

> [!question]- A tensor-network simulation reproduces a 100-qubit Rydberg quench. Does that deflate the experiment?
> Check the entanglement clock, not the qubit count. A short or near-adiabatic quench generates little entanglement — the state never left the MPS corner and classical simulation was guaranteed. Advantage claims live where $S(t)$ outruns any feasible $D$ before decoherence outruns the experiment: a race between bond dimension and $T_2$, which is why both numbers appear in every claim-and-rebuttal cycle.

# Connections

- [[Singular Value Decomposition]] — truncation = optimal low-rank approximation
- [[Entanglement Measures]] — the entropy that sets the cost
- [[Trotter Product Formula]] — TEBD's decomposition
- [[Exact Diagonalization and Sparse Methods]] — the exact validator below 20 qubits
- [[Tensor Product]] — the Hilbert-space structure being compressed
- [[Normal Modes of Ion Chains]] — the 1D systems simulated at scale

---
Source: Schollwöck, *Ann. Phys.* 326, 96 (2011); Orús, *Ann. Phys.* 349, 117 (2014)
