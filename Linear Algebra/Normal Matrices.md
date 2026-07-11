#linear-algebra #math

**$[A, A^\dagger] = 0$ — exactly the matrices that diagonalize in an orthonormal basis.** Normality is the precise price of admission to the spectral theorem: commute with your own adjoint, get a clean eigenbasis.

# Reference

$$
A A^\dagger = A^\dagger A \quad\Longleftrightarrow\quad A = U D U^\dagger \text{ for some unitary } U, \text{ diagonal } D
$$

The "iff" is the whole content: **normal ⇔ unitarily diagonalizable** ([[Spectral Theorem]]). Non-normal matrices may still diagonalize, but only with a skewed (non-orthogonal) eigenbasis — or not at all.

**The family tree** (all normal, distinguished by where eigenvalues live):

| Class | Constraint | Eigenvalues |
|---|---|---|
| Hermitian | $A = A^\dagger$ | real axis |
| Anti-Hermitian | $A = -A^\dagger$ | imaginary axis |
| Unitary | $A^\dagger = A^{-1}$ | unit circle |
| General normal | $[A,A^\dagger]=0$ | anywhere in $\mathbb{C}$ |

**Physical reading:** the operators you care about in QM — observables, evolution, density matrices — are all normal, which is why "expand in the eigenbasis" is a reflex that always works there. The trap is non-normal operators ($a$, $\sigma_+$, Lindbladian superoperators): eigenvectors need not be orthogonal, and transient dynamics can grow even when all eigenvalues say decay.

> [!question]- $\sigma_+ = |1\rangle\langle 0|$ has all eigenvalues zero. Why doesn't the spectral theorem force it to be the zero matrix?
> $\sigma_+$ isn't normal: $[\sigma_+, \sigma_-] = \sigma_z \ne 0$. No orthonormal eigenbasis exists — it's defective (one eigenvector for a 2×2 matrix), so $A = \sum\lambda_i|v_i\rangle\langle v_i|$ never applies.

# Connections

- [[Spectral Theorem]] — normality is its exact hypothesis
- [[Hermitian Matrices]] — the most-used special case (observables)
- [[Unitary Matrices]] — the other workhorse special case (evolution)
- [[Diagonalization]] — the general theory when you drop orthonormality

---
Source: Horn & Johnson, *Matrix Analysis*, §2.5.
