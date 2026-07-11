#linear-algebra #math

**Stack the columns of a density matrix into one long vector, and every "matrix acting on both sides of $\rho$" operation becomes a single matrix acting on that vector** — open-system dynamics turns back into ordinary linear algebra you can diagonalize.

# Reference

Vectorize: $\rho \to |\rho\rangle\rangle$, columns stacked ($d\times d$ matrix $\to d^2$ vector). The one identity that does all the work:
$$
A\rho B \;\longrightarrow\; (B^{T} \otimes A)\,|\rho\rangle\rangle
$$
(column-stacking convention; row-stacking swaps to $A \otimes B^T$ — check your convention before debugging signs).

**Why bother:** the Lindblad equation $\dot\rho = \mathcal{L}[\rho]$ is linear in $\rho$ but sandwiches it from both sides. Vectorized, it becomes $|\dot\rho\rangle\rangle = L\,|\rho\rangle\rangle$ with the $d^2 \times d^2$ Liouvillian
$$
L = -i\left(\mathbb{1}\otimes H - H^{T}\otimes \mathbb{1}\right) + \sum_k \left[\bar{L}_k \otimes L_k - \tfrac{1}{2}\mathbb{1}\otimes L_k^\dagger L_k - \tfrac{1}{2} (L_k^\dagger L_k)^{T} \otimes \mathbb{1}\right]
$$
Then $|\rho(t)\rangle\rangle = e^{Lt}|\rho(0)\rangle\rangle$: steady state = null vector of $L$, decay rates and oscillation frequencies = the rest of its spectrum (eigenvalues have $\mathrm{Re}\,\lambda \le 0$; $L$ is not Hermitian, expect complex pairs).

**Same trick, static problems:** Sylvester equations $AX + XB = C$ vectorize to $(\mathbb{1}\otimes A + B^T \otimes \mathbb{1})|X\rangle\rangle = |C\rangle\rangle$.

A quantum channel in this representation is just a $d^2\times d^2$ matrix (the "transfer matrix"); composing channels = multiplying matrices. This is what QuTiP et al. do under the hood when you call `to_super`.

> [!question]- Why does $A\rho B$ pick up a transpose on $B$ when vectorized?
> Column-stacking means right-multiplication by $B$ mixes *columns* of $\rho$ — in the stacked vector that's an action on the "which column" index, and tracking the index shuffle through $\mathrm{vec}(A\rho B) = (B^T\otimes A)\mathrm{vec}(\rho)$ forces the transpose. Wrong-convention transposes are the classic superoperator bug.

# Connections

- [[Lindblad Master Equation]] — the equation this machinery exists to solve; spectrum of $L$ gives all rates
- [[Quantum Channels]] — a channel is a matrix on vectorized state space; composition becomes multiplication
- [[Kraus Operators]] — each Kraus term $K\rho K^\dagger$ vectorizes to $\bar{K}\otimes K$
- [[Tensor Product]] — the Kronecker structure that makes the two-sided action expressible

---
Source: Wiseman & Milburn, *Quantum Measurement and Control*, App. B; Wood, Biamonte & Cory, arXiv:1111.6950
