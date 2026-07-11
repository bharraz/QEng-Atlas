#linear-algebra #math

**Any matrix — rectangular, defective, whatever — factors as rotation × nonnegative stretch × rotation: $A = U\Sigma V^\dagger$.** Where eigendecomposition needs a square, normal matrix, the SVD always exists. It's the honest answer to "what does this matrix actually do."

# Reference

For any $m \times n$ matrix $A$:

$$
A = U \Sigma V^\dagger = \sum_i \sigma_i\, |u_i\rangle\langle v_i|
$$

where $U$ ($m\times m$) and $V$ ($n\times n$) are unitary and $\Sigma$ holds the **singular values** $\sigma_1 \ge \sigma_2 \ge \cdots \ge 0$. Geometrically: $A$ maps the unit sphere to an ellipsoid; the $\sigma_i$ are the semi-axes, $v_i$ the input directions, $u_i$ where they land.

**Relation to eigenvalues:** $\sigma_i = \sqrt{\lambda_i(A^\dagger A)}$; the $v_i$ are eigenvectors of $A^\dagger A$, the $u_i$ of $AA^\dagger$. For Hermitian $A$, $\sigma_i = |\lambda_i|$. In general singular values ≠ |eigenvalues| — a non-normal matrix can have tiny eigenvalues but huge singular values (transient growth).

**Eckart–Young (low-rank approximation):** truncating to the top $k$ terms of $\sum_i \sigma_i |u_i\rangle\langle v_i|$ gives the best rank-$k$ approximation in both operator and Frobenius norm. This is PCA, image compression, and noise filtering in one theorem — the tail singular values are the part you can safely drop.

**Schmidt decomposition is the SVD in disguise:** reshape a bipartite state $|\psi\rangle = \sum_{ij} c_{ij}|i\rangle|j\rangle$ into the matrix $c$; its SVD gives $|\psi\rangle = \sum_k \sigma_k |u_k\rangle|v_k\rangle$. Number of nonzero $\sigma_k$ = Schmidt rank; more than one ⇒ entangled.

> [!question]- Why does the SVD of the coefficient matrix immediately reveal whether a bipartite pure state is entangled?
> Schmidt form $|\psi\rangle = \sum_k \sigma_k|u_k\rangle|v_k\rangle$ *is* the SVD of $c_{ij}$. Product state ⇔ $c$ has rank 1 ⇔ single nonzero singular value. The $\sigma_k^2$ are the reduced-state eigenvalues — entanglement entropy reads straight off the singular values.

# Connections

- [[Entanglement Measures]] — Schmidt coefficients = singular values; entanglement entropy comes from them
- [[Pseudo-Inverse]] — invert the nonzero $\sigma_i$, transpose the rotations: least-squares for free
- [[Condition Number]] — $\kappa = \sigma_{\max}/\sigma_{\min}$, read directly off the SVD
- [[Rank and Nullity]] — rank = number of nonzero singular values (the numerically robust definition)
- [[Polar Decomposition]] — regroup $U\Sigma V^\dagger = (UV^\dagger)(V\Sigma V^\dagger)$: rotation × stretch

---
Source: Horn & Johnson, *Matrix Analysis*, Ch. 7; Nielsen & Chuang §2.1.10 (Schmidt).
