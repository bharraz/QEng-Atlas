#numerics #quantum-info

**Below ~20 qubits, just build the Hamiltonian and diagonalize — but "just" hides three multipliers that decide whether your laptop or no computer on Earth can do it: sparsity (never store the dense matrix), Krylov methods (never diagonalize fully when you need one state or one trajectory), and symmetry (never work in a bigger space than the physics uses).** Exact diagonalization is the ground truth every approximate method (and many experiments) is validated against.

# Reference

**The arithmetic first.** $N$ qubits → dimension $2^N$. State vector at float64 complex: $2^N \times 16$ B — 16 GB at $N = 30$. A *dense* Hamiltonian squares that: 16 GB at $N = 15$, and dense diagonalization costs $O(8^N)$ time. The dense route dies at ~14–15 qubits; everything past that is structure exploitation.

**Sparsity.** Physical Hamiltonians are sums of few-body terms: each Pauli string maps a basis state to *one* other basis state, so $H$ has ~$N_{\text{terms}}$ nonzeros per row, not $2^N$. Stored sparse (CSR) — or better, never stored: a matrix-free function computing $H|\psi\rangle$ on the fly (apply each term's bit-flips/signs directly to the state array) costs $O(N_{\text{terms}} 2^N)$ per application and almost no memory beyond the vector. QuTiP/QuSpin/sparse-SciPy do this under the hood; writing your own matvec is often the fastest route for a specific model.

**Krylov methods — everything from matvecs alone.** The span $\{|\psi\rangle, H|\psi\rangle, H^2|\psi\rangle, \dots\}$ contains excellent approximations to whatever you actually want:

- **Ground state / low excitations:** **Lanczos** (Hermitian; `eigsh(H, k=6, which='SA')`) converges extreme eigenvalues in tens-to-hundreds of matvecs — $N = 24$–30 ground states are routine where full spectra are impossible. Two footnotes that bite: interior eigenvalues converge terribly (use shift-invert), and finite-precision Lanczos produces *ghost* duplicate eigenvalues (the library handles it; hand-rolled versions must reorthogonalize).
- **Dynamics:** $e^{-iHt}|\psi\rangle$ via `expm_multiply` / Krylov propagators — short-time-exact stepping using only matvecs; never form $e^{-iHt}$ ($2^N \times 2^N$ dense — see [[Matrix Exponential]]). This plus matrix-free $H$ is how 25+-qubit quench dynamics are computed exactly. For time-dependent/driven $H(t)$, combine with Magnus/commutator-free steps ([[Reference Atlas/Math/Magnus Expansion]]).
- The same machinery runs Liouvillians ([[Lindblad Master Equation]]) — dimension $4^N$, so the ceiling drops to ~12–13 qubits; beyond that, quantum trajectories (stochastic unfolding, $2^N$ per trajectory, embarrassingly parallel) beat the density matrix.

**Symmetry — block-diagonalize before you diagonalize.** If $[H, G] = 0$, eigenstates sort into $G$'s sectors and $H$ never mixes them ([[Simultaneous Diagonalization]], and the payoff of [[Symmetry in Quantum Mechanics]] as *engineering*): conserve total $S_z$ / excitation number → restrict to the fixed-Hamming-weight subspace ($\binom{N}{N/2}$ vs $2^N$: ~30× at $N=20$, and the [[Jaynes-Cummings Model|JC]]/spin-boson ladders reduce to per-excitation blocks); translation symmetry → momentum sectors ($\times N$ savings); parity, point-group sectors likewise. The mechanics: build the basis of one sector (hash table from bit patterns to indices), express $H$ within it. Symmetry sectors are also physics — level statistics *within* a sector distinguish integrable from chaotic; mixing sectors buries that signal.

**Truncation as silent ED:** bosonic modes get a Fock-space cutoff $n_{\max}$ — always converge in $n_{\max}$ like any other parameter (coherent/thermal states need $n_{\max} \gtrsim \bar n + 5\sqrt{\bar n}$; driven and squeezed dynamics climb higher than intuition suggests, and a truncation artifact looks exactly like physics: population piling at the cutoff reflects back).

**Checklist:** memory arithmetic *first* ($2^N \times 16$ B, ×2 for workspace); Hermitian solver for Hermitian matrix; converged in $k$, tolerance, boson cutoff; validated against a small case solved densely; sectors exploited, and results labeled by sector.

> [!question]- Your Lanczos ground-state energy is converged to 10 digits, but the correlation functions computed from the eigenvector look wrong. What's the classic cause?
> Degeneracy. Lanczos returns *an* arbitrary vector in a degenerate (or near-degenerate) ground-state manifold — energies converge beautifully while the vector is an uncontrolled mixture whose correlators are basis-dependent junk. Standard in symmetry-broken or topological phases where the manifold is 2+-dimensional. Fix: resolve the degeneracy — diagonalize the symmetry operators within the returned subspace (ask for several vectors, `k > 1`), or add a tiny symmetry-breaking field and extrapolate it away. The energy converging is not the calculation converging.

# Connections

- [[Tensor Networks and MPS]] — where to go when $2^N$ wins; ED is its validator below 20 qubits
- [[Matrix Exponential]] — why propagators are applied, never formed
- [[Reference Atlas/Math/Magnus Expansion]] — stepping driven Hamiltonians within the Krylov framework
- [[Simultaneous Diagonalization]] / [[Symmetry in Quantum Mechanics]] — the sector machinery
- [[Lindblad Master Equation]] — the $4^N$ version and the trajectory escape
- [[Floating Point and Numerical Error]] — Lanczos ghosts are its loss-of-orthogonality story

---
Source: Sandvik, "Computational studies of quantum spin systems," *AIP Conf. Proc.* 1297, 135 (2010), Sec. 4; Weinberg & Bukov, QuSpin papers (SciPost Phys. 2, 003; 7, 020)
