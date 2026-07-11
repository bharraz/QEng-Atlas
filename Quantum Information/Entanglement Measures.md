#quantum-info

**Quantify entanglement by how mixed a subsystem looks: write the state in its Schmidt form and take the entropy of the coefficients.** A pure global state with a mixed marginal is entangled — the missing purity went into correlations.

# Reference

**Schmidt decomposition** (SVD of the coefficient matrix $\psi_{ij}$):

$$
|\psi\rangle_{AB} = \sum_i \sqrt{\lambda_i}\,|i_A\rangle|i_B\rangle, \qquad \lambda_i \ge 0,\ \textstyle\sum\lambda_i = 1
$$

Product state $\Leftrightarrow$ Schmidt rank 1. Both marginals share the same spectrum $\{\lambda_i\}$.

**Entanglement entropy** (pure states — THE measure):

$$
S(\rho_A) = -\mathrm{Tr}\,\rho_A \log_2 \rho_A = -\sum_i \lambda_i \log_2 \lambda_i
$$

Bell state: $\lambda = \{\tfrac12,\tfrac12\}$ → 1 ebit. Max for $d$ levels: $\log_2 d$.

**Mixed states are harder**: separable means $\rho = \sum_k p_k\, \rho_A^k \otimes \rho_B^k$ — classically correlated only. Deciding separability is NP-hard in general; partial transpose (PPT) is the workhorse test. For **two qubits** there's a closed form: concurrence $C = \max(0, \mu_1-\mu_2-\mu_3-\mu_4)$ from the eigenvalues of $\sqrt{\rho\tilde\rho}$ (Wootters).

**Monogamy**: maximally entangled with one partner ⇒ zero entanglement with everything else — you can't share ebits the way you share classical correlations.

> [!question]- Why is $S(\rho_A)$ meaningless as an entanglement measure for mixed global states?
> A thermal product state already has $S(\rho_A)>0$ from classical uncertainty — subsystem entropy can't distinguish "entangled with B" from "just mixed". For pure $|\psi\rangle_{AB}$, mixedness of $\rho_A$ has nowhere else to come from.

# Connections

- [[Singular Value Decomposition]] — Schmidt decomposition is the SVD wearing bra-ket clothing
- [[Bell States]] — the 1-ebit calibration points
- [[Density Matrix]] — partial trace produces the $\rho_A$ everything here is computed from
- [[Trace Identities]] — the partial-trace machinery

---
Source: Preskill, Ph219 lecture notes, Ch. 4 (Quantum Entanglement)
