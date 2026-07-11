#linear-algebra #math

**Any matrix = rotation × stretch: $A = UP$ with $U$ unitary and $P$ positive semidefinite — the matrix version of $z = e^{i\theta}|z|$.** Separate what a matrix does into "how it reorients" and "how it deforms."

# Reference

$$
A = U P, \qquad P = \sqrt{A^\dagger A}
$$

$P$ is the unique PSD "modulus" of $A$; $U$ is unitary, unique when $A$ is invertible ($U = AP^{-1}$). Left-handed variant: $A = P'U$ with $P' = \sqrt{AA^\dagger}$ — same $U$, and $P' = UPU^\dagger$ (stretch first vs stretch after, in rotated axes).

**From the SVD in one line:** $A = U_s\Sigma V^\dagger = (U_s V^\dagger)(V\Sigma V^\dagger) = U\,P$. So polar and singular value decompositions carry the same information, regrouped.

**Where it earns its keep:**
- **Closest unitary:** $U$ is the unitary nearest to $A$ (in Frobenius norm) — the right way to "re-unitarize" a numerically drifted evolution operator or snap a fitted gate matrix back onto the unitary group.
- **Fidelity:** the trace norm $\|A\|_1 = \mathrm{Tr}\sqrt{A^\dagger A} = \mathrm{Tr}\,P$ underlying $F(\rho,\sigma)$ is the polar $P$'s trace.
- **Continuum mechanics analogue:** deformation gradient = rotation × strain; same theorem.

> [!question]- Your simulated time-evolution operator has drifted from unitarity by numerical error. Why is the polar $U$ the principled fix?
> $U = A(\sqrt{A^\dagger A})^{-1}$ is the *closest* unitary to $A$ — it keeps all the rotational content and discards exactly the spurious stretch $P \ne \mathbb{1}$ that error introduced. (Cheaper than SVD: iterate $X \leftarrow \tfrac{1}{2}(X + X^{-\dagger})$.)

# Connections

- [[Singular Value Decomposition]] — same decomposition regrouped: $U = U_sV^\dagger$, $P = V\Sigma V^\dagger$
- [[Positive Semidefinite Matrices]] — the stretch factor $P$ lives here; $\sqrt{A^\dagger A}$ needs the PSD square root
- [[Unitary Matrices]] — the rotation factor, and the target when projecting back onto "physical evolution"
- [[State and Gate Fidelity]] — $\mathrm{Tr}\sqrt{A^\dagger A}$ in the fidelity formula is polar decomposition at work

---
Source: Horn & Johnson, *Matrix Analysis*, §7.3; Nielsen & Chuang §2.1.10.
