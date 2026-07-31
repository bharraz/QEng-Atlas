#numerics

**A sparse matrix stores only its nonzeros; cost scales with their count (nnz) instead of $n^2$.** The working questions: which format for which access pattern, which operations preserve sparsity (several common ones silently do not), and when to abandon storage for a matrix-free product.

# Reference

**When sparse wins.** Dense storage $n^2 \times 16$ B (complex float64) vs sparse $\sim$ nnz $\times$ 20 B; matvec $O(n^2)$ vs $O(\text{nnz})$. Break-even ~5–10% density; the useful regime is ≪1% — a $10^6$-dimensional Hamiltonian with 100 nonzeros/row is 8 TB dense, 2 GB sparse. Local operators are sparse in a local basis (few-body Hamiltonians; a finite-difference Laplacian on $N$ points: nnz $\approx 3N$); the same operator can be dense in another basis — basis choice is a sparsity decision.

**Formats** (SciPy names):

| format | layout | fast | slow |
|---|---|---|---|
| COO | (row, col, value) triplets | construction, conversion | arithmetic |
| CSR | rows compressed | matvec $Ax$, row slicing | column access, editing |
| CSC | columns compressed | $A^{\top}x$, column slicing, direct solvers | row access, editing |
| LIL/DOK | per-row lists / dict | incremental editing | arithmetic |
| DIA | diagonals only | banded solves ($O(n)$ tridiagonal) | anything off-band |

Workflow: build in COO/LIL → convert to CSR/CSC to compute. Writing single entries into CSR reallocates its arrays — element-wise construction in CSR is quadratic in practice.

**Sparsity bookkeeping:**

- Preserved: $A + B$ (same pattern), $cA$, matvec, sparse×sparse (denser but structured).
- Destroyed by design: $A^{-1}$ is generically dense — solve $Ax = b$, never invert ([[Floating Point and Numerical Error]]); matrix functions ($e^A$, [[Matrix Exponential]]) likewise — apply to vectors instead.
- Destroyed silently: adding a scalar or dense array, element-wise $f$ with $f(0) \neq 0$, library fallbacks. Symptom: memory spike; check: nnz and object type after each step of a new pipeline.

**Solving $Ax = b$:**

- **Direct** (sparse LU/Cholesky): factor once, solve many; exact. Cost = **fill-in** — the factors are denser than $A$, dependent on elimination order (solvers permute to minimize it; banded/tree-structured systems fill almost nothing). Fine for 1D/2D-sized problems; fill kills 3D.
- **Iterative** (CG for symmetric positive definite; GMRES/BiCGSTAB general): matvecs only, memory stays $O(\text{nnz})$; iteration count grows with the [[Condition Number|condition number]] ($\sqrt{\kappa}$ for CG). A **preconditioner** $M^{-1} \approx A^{-1}$, cheap to apply (incomplete factorization, diagonal, physics-informed), replaces $\kappa(A)$ by $\kappa(M^{-1}A)$ — routinely the difference between 30 and 30 000 iterations.
- Eigenproblems split the same way: dense solvers below $\sim 10^4$, Lanczos/Arnoldi above ([[Exact Diagonalization and Sparse Methods]]).

**Matrix-free.** If $x \mapsto Ax$ is computable from the operator's definition (local terms applied to a state array, FFT for convolution/kinetic terms, a stencil), no matrix need exist; all Krylov machinery accepts a function (`LinearOperator`). Fastest and smallest, at the cost of hand-validating the product against an explicitly built small case.

> [!question]- A sparse pipeline that ran in seconds at $n = 10^4$ hangs at $10^6$ with memory climbing. The two usual suspects?
> Silent densification (scalar add, element-wise function, dense fallback — check nnz/type per step) or direct-solver fill-in (a matrix that fits does not imply its factors fit). Fixes: restructure the offending step to act on stored values only; or switch to a preconditioned iterative solver, or exploit band/tree structure. More RAM fixes neither at any scale worth having.

# Connections

- [[Exact Diagonalization and Sparse Methods]] — sparse and matrix-free Hamiltonians in use
- [[Floating Point and Numerical Error]] — solve-don't-invert; conditioning
- [[Condition Number]] — iterative convergence rates
- [[Matrix Exponential]] — dense result; apply, don't form
- [[Tensor Networks and MPS]] — the complementary compression (state, not operator)

---
Source: Davis, *Direct Methods for Sparse Linear Systems*; Saad, *Iterative Methods for Sparse Linear Systems*, Ch. 3–4, 9–10
