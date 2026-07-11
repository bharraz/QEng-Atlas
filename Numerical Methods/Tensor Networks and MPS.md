#numerics #quantum-info

**A many-body wavefunction needs $2^N$ numbers in general — but physically relevant states (ground states of local Hamiltonians, short quenches) are only weakly entangled, and a matrix product state stores exactly that corner of Hilbert space with $\sim N D^2$ numbers, where the bond dimension $D$ meters the entanglement kept.** Tensor networks are lossy compression whose compression ratio is set by an entanglement law — and the reason 50-qubit-scale ion/Rydberg experiments can (sometimes) be simulated classically.

# Reference

**The construction is iterated [[Singular Value Decomposition|SVD]].** Cut an $N$-qubit state between sites $k$ and $k{+}1$; the Schmidt decomposition $|\psi\rangle = \sum_\alpha \lambda_\alpha |L_\alpha\rangle|R_\alpha\rangle$ has as many terms as the entanglement across the cut demands ($S = -\sum \lambda_\alpha^2 \ln \lambda_\alpha^2$). Do this at every bond, keep only the $D$ largest Schmidt values per cut, and the state factorizes into a chain of tensors:

$$\psi_{s_1 s_2 \cdots s_N} = A^{s_1}_{[1]} A^{s_2}_{[2]} \cdots A^{s_N}_{[N]},$$

each $A^{s_k}$ a $D\times D$ matrix (hence *matrix product state*). Truncation error = discarded Schmidt weight — controlled, measurable, and the single convergence knob: **rerun with larger $D$; if observables move, you were truncating physics.**

**Why it works — the area law.** Ground states of gapped local 1D Hamiltonians have entanglement *independent of system size* (area law): constant $D$ suffices for arbitrarily large $N$. That's the miracle. Conversely, everything that fails follows from the same accounting: critical points ($S \sim \ln N$, $D$ grows polynomially — fine), 2D systems (area law now means $S \sim$ boundary length: $D \sim e^{L}$ for an $L$-wide cylinder — the practical ceiling of "2D DMRG"), and **quench dynamics** ($S$ grows *linearly* in time after a global quench → $D$ must grow exponentially in $t$: MPS simulates short-time dynamics superbly and long-time dynamics not at all — this, not qubit count, is where classical simulability of quantum experiments actually dies).

**The algorithm names decoded** (what the packages — ITensor, TeNPy, quimb — do):
- **DMRG**: variational ground-state search over MPS, sweeping site by site, each local update an eigenproblem (via [[Exact Diagonalization and Sparse Methods|Lanczos]]). The most accurate method in existence for 1D ground states — energies to 10⁻¹⁰ routinely.
- **TEBD / TDVP**: time evolution — Trotterize $e^{-iHt}$ into local gates ([[Trotter Product Formula]]), apply, re-truncate by SVD each step (TEBD); or project the Schrödinger equation onto the MPS manifold (TDVP, better for long-range terms). Also imaginary time → thermal states.
- **MPO**: operators in the same chain form; Hamiltonians of local + power-law terms compress to tiny MPOs (this is how long-range ion-chain $J_{ij} \sim 1/r^\alpha$ Hamiltonians are handled).
- **Beyond chains:** PEPS (2D generalization, expensive contractions), tree networks/MERA (critical systems, holography-adjacent literature), and tensor-network *circuit* simulators — the "quantum supremacy spoofing" literature is contraction-order optimization on the circuit's network.

**Reading-the-literature glossary:** *bond dimension* $D$ (also χ) — entanglement kept; *truncation/discarded weight* — the error meter; *canonical form* — the gauge that makes truncation optimal and local measurements cheap; *entanglement spectrum* — the Schmidt values themselves, now used as a diagnostic (degeneracies signal topological order); *area law* — the compressibility criterion; *volume law* — the death sentence.

**When to reach for it** (vs [[Exact Diagonalization and Sparse Methods|ED]]): ED is exact and unstructured but caps at ~20 qubits (state vector) — use it below that and for validation. MPS handles hundreds of sites in 1D when entanglement is low. Neither helps deep 2D or long-time dynamics — that's QMC (sign problem permitting) or an actual quantum simulator; knowing *which side of the line an experiment sits on* is precisely the classical-vs-quantum-advantage question the field argues about.

> [!question]- A tensor-network simulation "verifies" a 100-qubit Rydberg quench experiment to good accuracy. Does that deflate the experiment's claim to quantum advantage?
> It's the right question and the answer is quantitative, not rhetorical: check the entanglement clock. If the quench was short, or the dynamics stayed near-adiabatic (gap open, low entanglement generation), the state never left the MPS-compressible corner and classical simulation was always going to work — the experiment demonstrated control, not classical intractability. Advantage claims live specifically where entanglement growth outruns any feasible $D$ before decoherence outruns the experiment — a race with the bond dimension on one side and $T_2$ on the other, which is why both numbers appear in every such paper's rebuttal cycle.

# Connections

- [[Singular Value Decomposition]] — the engine: truncation is optimal low-rank approximation
- [[Tensor Product]] — the Hilbert-space structure being compressed
- [[Entanglement Measures]] — Schmidt/entanglement entropy as the compression criterion
- [[Trotter Product Formula]] — TEBD's decomposition of time evolution
- [[Exact Diagonalization and Sparse Methods]] — the exact small-system complement and validator
- [[Normal Modes of Ion Chains]] — the 1D systems these methods simulate at scale

---
Source: Schollwöck, "The DMRG in the age of MPS," *Ann. Phys.* 326, 96 (2011); Orús, *Ann. Phys.* 349, 117 (2014); Cirac et al., *Rev. Mod. Phys.* 93, 045003 (2021)
