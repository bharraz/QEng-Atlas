#linear-algebra #math

**The composite-system construction: dimensions multiply, and operators act on their own factor — $(A\otimes B)(u\otimes v) = Au \otimes Bv$.** Two qubits don't live in $2+2=4$... they live in $2\times 2 = 4$, and for $n$ qubits that's $2^n$ — the exponential blowup that makes quantum hard to simulate and worth building.

# Reference

For $|u\rangle \in \mathcal{H}_A$ ($\dim m$), $|v\rangle \in \mathcal{H}_B$ ($\dim n$): $|u\rangle\otimes|v\rangle \in \mathcal{H}_A\otimes\mathcal{H}_B$ ($\dim mn$). Basis: all products $|i\rangle_A|j\rangle_B$. Operators:

$$
(A \otimes B)(|u\rangle \otimes |v\rangle) = A|u\rangle \otimes B|v\rangle, \qquad (A\otimes B)(C\otimes D) = AC \otimes BD
$$

"$A$ on qubit 1 alone" means $A \otimes \mathbb{1}$ — the identity padding is implicit in physics notation but not in your code.

**Kronecker product** (the concrete matrix form — each entry of the left factor scales a full copy of the right):

$$
A \otimes B = \begin{pmatrix} a_{11}B & a_{12}B \\ a_{21}B & a_{22}B \end{pmatrix},
\qquad e.g.\;\;
\sigma_z \otimes \sigma_x = \begin{pmatrix} 0&1&0&0 \\ 1&0&0&0 \\ 0&0&0&-1 \\ 0&0&-1&0 \end{pmatrix}
$$

Ordering convention (left factor = most significant index) must match your basis ordering $|00\rangle, |01\rangle, |10\rangle, |11\rangle$ — the classic source of silently wrong two-qubit simulations.

**Useful algebra:** $\mathrm{Tr}(A\otimes B) = \mathrm{Tr}A\cdot\mathrm{Tr}B$; $(A\otimes B)^\dagger = A^\dagger\otimes B^\dagger$; eigenvalues of $A\otimes B$ = all products $\lambda_i\mu_j$.

**Entanglement = failure to factor:** generic $|\psi\rangle \in \mathcal{H}_A\otimes\mathcal{H}_B$ is *not* $|u\rangle\otimes|v\rangle$. Product states are a measure-zero set; the rest are entangled — quantified by the Schmidt decomposition.

> [!question]- Why can't $(|00\rangle + |11\rangle)/\sqrt{2}$ be written as $|u\rangle\otimes|v\rangle$?
> Expand $|u\rangle\otimes|v\rangle = (a|0\rangle+b|1\rangle)(c|0\rangle+d|1\rangle)$: need $ac = bd = 1/\sqrt 2$ but $ad = bc = 0$. The products $ac\cdot bd \ne ad\cdot bc$ — contradiction, since both equal $abcd$. Coefficient matrix has rank 2: entangled.

# Connections

- [[Qubits]] — $n$ of them = $(\mathbb{C}^2)^{\otimes n}$: where the $2^n$ comes from
- [[Entanglement Measures]] — quantifying non-product-ness via Schmidt/SVD of the coefficient matrix
- [[Trace Identities]] — partial trace: the inverse operation, from composite back to subsystem
- [[Vectorization and Superoperators]] — the vec trick turns superoperators into tensor products

---
Source: Nielsen & Chuang §2.1.7.
