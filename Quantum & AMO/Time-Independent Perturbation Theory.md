#quantum

**Take a Hamiltonian $H_0$ you can solve exactly, add a small coupling $V$, and correct its energies and eigenstates order by order: to first order each energy moves by the diagonal element of $V$, and to second order every other state it couples to pushes it away.** The expansion parameter is always $V_{mn}/(E_n - E_m)$, a coupling divided by the energy gap it bridges, so the method works when couplings are small compared with level spacings, and fails near a degeneracy.

# Reference

$H = H_0 + \lambda V$, for a nondegenerate level $|n^{(0)}\rangle$:

$$
E_n^{(1)} = \langle n^{(0)}|V|n^{(0)}\rangle, \qquad
E_n^{(2)} = \sum_{m\neq n}\frac{|\langle m^{(0)}|V|n^{(0)}\rangle|^2}{E_n^{(0)} - E_m^{(0)}}
$$

$$
|n^{(1)}\rangle = \sum_{m\neq n}\frac{\langle m^{(0)}|V|n^{(0)}\rangle}{E_n^{(0)} - E_m^{(0)}}\,|m^{(0)}\rangle
$$

- $\lvert n^{(0)}\rangle$, $E_n^{(0)}$ — eigenstates and energies of $H_0$
- $V$ — the perturbation (J); $\lambda$ counts its order
- $E_n^{(1)}, E_n^{(2)}$ — first- and second-order energy corrections (J)
- $\lvert n^{(1)}\rangle$ — first-order admixture of the other states

**Picture:** coupled levels repel like the normal modes of two coupled pendulums — the coupling pushes the two frequencies apart, and the closer they started, the harder they are pushed.

**Second-order sign structure — levels repel.** For the ground state every denominator is negative, so $E_0^{(2)} \leq 0$ always. Any pair of coupled levels pushes apart; a level shifts *away* from whatever it couples to. This predicts the sign of light shifts, quadratic Zeeman and Stark shifts, and dispersive qubit–cavity pulls without computing anything.

**State mixing.** Each admixture is of order $V_{mn}/\Delta E$, the same ratio that must be $\ll 1$ for the series to converge. When it is not, you are near a degeneracy.

**Degenerate case.** The formulas diverge as $\Delta E \to 0$. The fix: **diagonalize $V$ within the degenerate subspace first**; the correct zeroth-order states are those eigenvectors, and the first-order energies are the eigenvalues of the projected $V$. The linear Stark effect in hydrogen's $n = 2$ level is the standard example: the degeneracy turns a second-order effect into a first-order one ([[Degeneracy and Level Crossings]]).

**Second-order couplings between two states.** If $V$ connects $|m\rangle$ and $|n\rangle$ only through intermediate states, second order also produces an effective coupling between them, $\sum_k V_{mk}V_{kn}/(E - E_k)$: the basis of Raman transitions, superexchange, and mediated spin–spin interactions ([[Effective Hamiltonians and Adiabatic Elimination]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| a shift linear in the applied field | a first-order effect: a nonzero diagonal element, or a degenerate manifold |
| a shift quadratic in the field | a second-order effect: coupling to other levels with no diagonal element |
| the sign of a quadratic shift | which coupled level is nearer, above or below |
| a weak transition that becomes allowed in a field | admixture of an allowed state, of order $V/\Delta E$ in amplitude and its square in strength |

> [!question]- Two levels 10 MHz apart get a coupling with $V_{mn}/h = 1$ MHz. Sketch what happens to each level and to the states.
> They repel by about $V^2/\Delta E = 100$ kHz each, shifting away from each other, and each state picks up a $V/\Delta E = 10\%$ amplitude admixture of the other. If the splitting were $\lesssim 1$ MHz you would switch to degenerate theory, or diagonalize the $2\times2$ exactly.

# Connections

- [[Stark Effect and Light Shifts]] — this method's most-used AMO output
- [[Time-Dependent Perturbation Theory]] — the same expansion when $V$ oscillates
- [[Two-Level Systems]] — the exact $2\times2$ answer perturbation theory approximates, and the fallback near degeneracy
- [[Rayleigh Quotient and Variational Principle]] — the complementary non-perturbative estimate
- [[Degeneracy and Level Crossings]] — degenerate perturbation theory and its consequences
- [[Effective Hamiltonians and Adiabatic Elimination]] — second-order couplings through intermediate states
- [[Reading Matrices and Hamiltonians]] — the coupling-over-gap comparison in matrix form

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §5.1–5.2
