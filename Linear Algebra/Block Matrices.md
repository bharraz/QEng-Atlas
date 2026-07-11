#linear-algebra #math

**Treat submatrices as if they were scalar entries and multiply blockwise — it works whenever the partition shapes are compatible.** Block structure is how symmetry shows up in a matrix: block diagonal means the dynamics never leaves a subspace.

# Reference

$$
\begin{pmatrix} A & B \\ C & D \end{pmatrix}
\begin{pmatrix} E & F \\ G & H \end{pmatrix}
=
\begin{pmatrix} AE+BG & AF+BH \\ CE+DG & CF+DH \end{pmatrix}
$$
— same pattern as $2\times 2$ scalars, but **order matters inside each product** (blocks don't commute).

**Block diagonal = invariant subspaces.** $H = \mathrm{diag}(H_1, H_2, \dots)$ means each subspace evolves independently: eigenvalues are the union of block eigenvalues, $e^{H} = \mathrm{diag}(e^{H_1}, e^{H_2}, \dots)$, determinant is the product. Finding the basis where a big matrix block-diagonalizes *is* finding its conserved quantum numbers — a Hamiltonian commuting with a symmetry splits into blocks labeled by that symmetry's eigenvalues (angular momentum sectors, parity sectors, excitation number in the RWA). Diagonalize the small blocks, never the whole thing.

**Off-diagonal blocks = coupling.** In $\begin{pmatrix} H_1 & V \\ V^\dagger & H_2 \end{pmatrix}$, $V$ is what connects the sectors — perturbation theory in $V$, avoided crossings, and adiabatic elimination all start from this partition.

**Schur complement one-liner:** eliminating the second block from $\begin{pmatrix} A & B\\ C & D\end{pmatrix}$ leaves an effective operator $A - BD^{-1}C$ on the first — the linear-algebra skeleton of adiabatic elimination and effective Hamiltonians (that's where second-order $|V|^2/\Delta$ shifts come from). Also gives $\det = \det(D)\det(A - BD^{-1}C)$.

> [!question]- Your Hamiltonian commutes with parity. What does that buy you computationally, in block language?
> In the parity eigenbasis $H$ is block diagonal — no matrix element connects even and odd sectors. You diagonalize two half-size blocks instead of the full matrix ($\sim 4\times$ cheaper for dense eigensolvers), and every eigenstate carries a definite parity label for free.

# Connections

- [[Projectors]] — blocks are what $P H P$, $P H Q$ look like once you pick projectors onto subspaces
- [[Simultaneous Diagonalization]] — a symmetry's eigenspaces provide the block structure
- [[Two-Level Systems]] — the $2\times 2$ coupled-sector partition, taken as the whole problem
- [[Time-Independent Perturbation Theory]] — the Schur complement is the exact version of the effective-Hamiltonian expansions

---
Source: Horn & Johnson, *Matrix Analysis*, §0.7-0.8
