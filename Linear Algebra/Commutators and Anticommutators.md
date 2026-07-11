#linear-algebra #math

**$[A,B] = AB - BA$ measures the failure of two operators to share order — and in QM, that failure is physics: uncertainty, dynamics, and quantum numbers all read off commutators.** $\{A,B\} = AB + BA$ is the symmetric partner, home of fermions and Pauli algebra.

# Reference

$$
[A,B] = AB - BA, \qquad \{A,B\} = AB + BA, \qquad AB = \tfrac{1}{2}[A,B] + \tfrac{1}{2}\{A,B\}
$$

**Algebra kit** (memorize the product rule; derive the rest):

$$
[A, BC] = [A,B]\,C + B\,[A,C] \qquad (\text{commutator acts like a derivative})
$$

- Bilinear, antisymmetric $[A,B] = -[B,A]$; $[A,B]^\dagger = [B^\dagger, A^\dagger]$ (so $i[A,B]$ is Hermitian when $A,B$ are)
- **Jacobi:** $[A,[B,C]] + [B,[C,A]] + [C,[A,B]] = 0$ — what makes commutators a Lie bracket
- $\mathrm{Tr}[A,B] = 0$ always

**The canonical commutator:**

$$
[x, p] = i\hbar
$$

— the axiom the rest of QM's structure hangs off; it forces infinite dimensions ($\mathrm{Tr}$ argument) and generates $[a, a^\dagger] = 1$.

**Uncertainty from noncommutation** (Robertson, one line): $\Delta A\, \Delta B \ge \tfrac{1}{2}|\langle [A,B]\rangle|$ — noncommuting observables can't be simultaneously sharp; $[x,p] = i\hbar$ gives $\Delta x\Delta p \ge \hbar/2$.

**Dynamics:** Heisenberg EOM $\dot{O} = \tfrac{i}{\hbar}[H, O]$ — commuting with $H$ ⇔ conserved. Commutators are the quantum shadow of Poisson brackets.

**Anticommutators:** fermionic ladder operators use $\{c_i, c_j^\dagger\} = \delta_{ij}$ (Pauli exclusion is $c^2 = 0$); distinct Pauli matrices anticommute — the origin of the commute-or-anticommute dichotomy in the Pauli group.

> [!question]- Derive $[A, BC] = [A,B]C + B[A,C]$ and say why "commutator = derivation" is the useful reading.
> Add and subtract $BAC$: $ABC - BCA = (AB{-}BA)C + B(AC{-}CA)$. Leibniz rule ⇒ computing $[A, \cdot]$ on any product means differentiating factor by factor — e.g. $[a, (a^\dagger)^n] = n(a^\dagger)^{n-1}$ falls out like a power rule.

# Connections

- [[Simultaneous Diagonalization]] — $[A,B]=0$ is exactly when common eigenbases (quantum numbers) exist
- [[Ladder Operators]] — $[a,a^\dagger]=1$ and eigenoperator relations $[H,a]=-\hbar\omega a$: commutators as the solving tool
- [[Baker-Campbell-Hausdorff]] — nested commutators as the currency of exponential manipulations
- [[Pauli Matrices]] — the compact case study: $[\sigma_i,\sigma_j]=2i\varepsilon_{ijk}\sigma_k$, $\{\sigma_i,\sigma_j\}=2\delta_{ij}$
- [[Heisenberg and Schrodinger Pictures]] — dynamics as commutation with $H$

---
Source: Nielsen & Chuang §2.1.5; Sakurai, *Modern QM*, Ch. 1.
