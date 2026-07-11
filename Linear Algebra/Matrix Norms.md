#linear-algebra #math

**A matrix norm is a single number answering "how big is this operator" — and the right answer depends on whether you care about the worst case, the average, or distinguishability of quantum states.**

# Reference

The three that matter, all expressible in singular values $\sigma_i$:

| Norm | Definition | In $\sigma_i$ | When it's the right one |
|---|---|---|---|
| Operator (spectral) | $\|A\| = \max_{x\neq 0} \|Ax\|/\|x\|$ | $\sigma_{\max}$ | worst-case amplification, stability, gate error bounds |
| Frobenius | $\sqrt{\mathrm{Tr}(A^\dagger A)}$ | $\sqrt{\sum_i \sigma_i^2}$ | average/RMS size, least-squares distance |
| Trace (nuclear) | $\mathrm{Tr}\sqrt{A^\dagger A}$ | $\sum_i \sigma_i$ | state distinguishability: $\tfrac12\|\rho-\sigma\|_1$ is trace distance |

These are the $p=\infty, 2, 1$ members of the Schatten family ($\ell_p$ norms on the singular value list). Ordering: $\|A\| \le \|A\|_F \le \|A\|_{\mathrm{tr}} \le \sqrt{r}\,\|A\|_F$ with $r$ the rank.

**Unitary invariance:** all three satisfy $\|UAV\| = \|A\|$ for unitary $U,V$ — the norm sees only the singular values, not the bases. This is why they're basis-independent measures of gate or channel error.

**Physics usage:** trace distance bounds the best measurement's ability to tell $\rho$ from $\sigma$; the operator norm of $U_{\mathrm{ideal}}^\dagger U_{\mathrm{actual}} - \mathbb{1}$ bounds worst-case gate error over all input states.

> [!question]- Your gate error is small in Frobenius norm but an experiment sees large errors for one particular input state. Which norm should you have quoted?
> The operator norm — it's the worst case over inputs, $\sigma_{\max}$. Frobenius averages over directions, so a single bad direction gets diluted by dimension.

# Connections

- [[Singular Value Decomposition]] — every unitarily invariant norm is a function of the singular values
- [[State and Gate Fidelity]] — fidelity and trace distance are the two standard closeness measures; Fuchs-van de Graaf ties them together
- [[Condition Number]] — the ratio $\sigma_{\max}/\sigma_{\min}$, i.e. operator norm of $A$ times that of $A^{-1}$

---
Source: Horn & Johnson, *Matrix Analysis*, Ch. 5; Nielsen & Chuang §9.2 for trace distance
