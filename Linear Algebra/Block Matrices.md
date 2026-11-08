#linear-algebra #math

**Group the basis states of a problem into sets — the states you care about and the rest, or the even and the odd — and the matrix splits into blocks: diagonal blocks act within a set, off-diagonal blocks connect sets.** Blocks multiply as if they were scalar entries, provided the order inside each product is kept. Block structure is how a symmetry shows up in a matrix: a block-diagonal Hamiltonian never moves amplitude between its blocks.

# Reference

$$
\begin{pmatrix} A & B \\ C & D \end{pmatrix}
\begin{pmatrix} E & F \\ G & H \end{pmatrix}
=
\begin{pmatrix} AE+BG & AF+BH \\ CE+DG & CF+DH \end{pmatrix}
$$

This is the same pattern as for $2\times 2$ scalars, but **order matters inside each product**, because blocks do not commute.

**Picture:** a building with separate wings — rooms connected by corridors inside each wing (the diagonal blocks) and a few bridges between wings (the off-diagonal blocks); remove the bridges and each wing is its own problem.

**Block diagonal = invariant subspaces.** $H = \mathrm{diag}(H_1, H_2, \dots)$ means each subspace evolves independently: eigenvalues are the union of the blocks' eigenvalues, $e^{H} = \mathrm{diag}(e^{H_1}, e^{H_2}, \dots)$, and the determinant is the product. Finding the basis where a large matrix block-diagonalizes is finding its conserved quantum numbers. A Hamiltonian commuting with a symmetry splits into blocks labelled by the symmetry's eigenvalues: angular momentum sectors, parity sectors, excitation number in the rotating-wave approximation ([[Symmetry in Quantum Mechanics]]). Diagonalize the small blocks, never the entire matrix.

**Off-diagonal blocks = coupling.** In $\begin{pmatrix} H_1 & V \\ V^\dagger & H_2 \end{pmatrix}$, $V$ is what connects the sectors. Perturbation theory in $V$, avoided crossings, and adiabatic elimination all start from this partition.

**Schur complement.** Eliminating the second block of $\begin{pmatrix} A & B\\ C & D\end{pmatrix}$ leaves an effective operator on the first:

$$
A - BD^{-1}C, \qquad \det\begin{pmatrix} A & B\\ C & D\end{pmatrix} = \det(D)\,\det(A - BD^{-1}C)
$$

For a Hamiltonian partitioned into a set $P$ and the rest $Q$, the exact statement is

$$
H_\text{eff}(E) = H_P + V\,(E - H_Q)^{-1}\,V^\dagger
$$

- $H_P$, $H_Q$ — diagonal blocks for the kept and eliminated states
- $V$ — off-diagonal block coupling them
- $E$ — the energy at which the eigenvalue problem is solved

The eigenvalues of $H$ in $P$ are the solutions of $H_\text{eff}(E)\,\psi = E\psi$. Replacing $E$ by the unperturbed energy of $P$ gives the second-order $|V|^2/\Delta$ shifts and couplings of [[Effective Hamiltonians and Adiabatic Elimination]].

> [!question]- Your Hamiltonian commutes with parity. What does that give you computationally, in block language?
> In the parity eigenbasis $H$ is block diagonal: no matrix element connects the even and odd sectors. You diagonalize two half-size blocks instead of the full matrix, roughly 4× cheaper for dense eigensolvers, and every eigenstate carries a definite parity label automatically.

# Connections

- [[Projectors]] — blocks are $PHP$, $PHQ$ once you pick projectors onto subspaces
- [[Simultaneous Diagonalization]] — a symmetry's eigenspaces provide the block structure
- [[Two-Level Systems]] — the $2\times 2$ coupled-sector partition, taken as the entire problem
- [[Time-Independent Perturbation Theory]] — the Schur complement is the exact version of its effective-Hamiltonian expansions
- [[Effective Hamiltonians and Adiabatic Elimination]] — the second-order form, applied
- [[Reading Matrices and Hamiltonians]] — what blocks mean for a Hamiltonian's dynamics

---
Source: Horn & Johnson, *Matrix Analysis*, §0.7–0.8; P.-O. Löwdin, *J. Math. Phys.* 3, 969 (1962) (partitioning technique)
