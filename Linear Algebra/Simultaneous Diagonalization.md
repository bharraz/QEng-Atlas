#linear-algebra #math

**Two diagonalizable operators share a common eigenbasis iff they commute — this is why "good quantum numbers" exist.** Labels like $n, l, m$ are simultaneous eigenvalues of a commuting set; noncommuting observables ($x$ and $p$) fundamentally can't share labels.

# Reference

For diagonalizable (in practice: Hermitian/normal) $A$, $B$:

$$
[A, B] = 0 \quad\Longleftrightarrow\quad \exists\ \text{basis } \{|v_i\rangle\}: \; A|v_i\rangle = a_i|v_i\rangle,\; B|v_i\rangle = b_i|v_i\rangle
$$

States get labeled by the eigenvalue pair $|a, b\rangle$ — quantum numbers are born. Extends to any mutually commuting family; a **CSCO** (complete set of commuting observables) is one whose joint eigenvalues label states uniquely, e.g. $\{H, L^2, L_z\}$ for hydrogen.

**The degeneracy caveat** — where hand-waving fails. If $A$ has a degenerate eigenvalue, its eigenbasis is *not* unique within the degenerate subspace, and a random eigenbasis of $A$ will generally *not* diagonalize $B$. Commuting only guarantees $B$ maps each eigenspace of $A$ into itself (block-diagonal); you must then diagonalize $B$ *within* each block to pick the shared basis. Practical recipe (also numerically): diagonalize $A$, then diagonalize $B$ restricted to each degenerate subspace — or cheat by diagonalizing $A + \epsilon B$.

**Conservation reading:** $[H, B] = 0$ ⇒ $B$'s eigenvalues are constants of motion (Heisenberg EOM $\dot{B} \propto [H,B] = 0$) — symmetry ⇒ good quantum number ⇒ selection rules.

> [!question]- $[A,B]=0$ and you've diagonalized $A$. Why might your eigenvectors fail to diagonalize $B$, and what's the fix?
> Degeneracy: within an eigenvalue-$a$ subspace of $A$, *any* orthonormal basis diagonalizes $A$, but only special ones diagonalize $B$. Fix: diagonalize $B$'s restriction to each degenerate block.

# Connections

- [[Commutators and Anticommutators]] — the commutator as the obstruction being tested
- [[Diagonalization]] — the single-operator machinery this builds on
- [[Spectral Theorem]] — supplies the orthonormal eigenbases for each Hermitian operator
- [[Angular Momentum in QM]] — $\{L^2, L_z\}$: the textbook commuting pair generating $l, m$ labels

---
Source: Horn & Johnson, *Matrix Analysis*, Thm 1.3.12; Nielsen & Chuang §2.1.9.
