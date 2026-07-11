#quantum

**Solve $H_0$ exactly, then correct energies and states order by order in the small coupling $V$ — energies to first order are just diagonal expectation values, and second order is level repulsion by every other state.** The small parameter is always $V_{mn}/(E_n - E_m)$.

# Reference

$H = H_0 + \lambda V$, nondegenerate level $|n^{(0)}\rangle$:

$$
E_n^{(1)} = \langle n^{(0)}|V|n^{(0)}\rangle, \qquad
E_n^{(2)} = \sum_{m\neq n}\frac{|\langle m^{(0)}|V|n^{(0)}\rangle|^2}{E_n^{(0)} - E_m^{(0)}}
$$

$$
|n^{(1)}\rangle = \sum_{m\neq n}\frac{\langle m^{(0)}|V|n^{(0)}\rangle}{E_n^{(0)} - E_m^{(0)}}\,|m^{(0)}\rangle
$$

**Second-order sign structure — levels repel:** for the ground state every denominator is negative, so $E_0^{(2)} \leq 0$ always. Any pair of coupled levels pushes apart; a level shifts *away* from whatever it couples to. This one fact predicts the sign of light shifts, quadratic Zeeman/Stark shifts, and dispersive qubit-cavity pulls without computing anything.

**State mixing:** each admixture $\sim V_{mn}/\Delta E$ — the same ratio that must be $\ll 1$ for the series to converge. When it isn't, you're near a degeneracy:

**Degenerate case:** naive formulas blow up ($\Delta E \to 0$ in denominators). Fix: **diagonalize $V$ within the degenerate subspace first**; the correct zeroth-order states are those eigenvectors, and the first-order energies are the eigenvalues of the projected $V$. (Linear Stark effect in hydrogen $n=2$ is the canonical example — degeneracy converts a second-order effect into first-order.)

> [!question]- Two levels 10 MHz apart get a coupling with $V_{mn}/h = 1$ MHz. Sketch what happens to each level and to the states.
> They repel by $\approx V^2/\Delta E = 100$ kHz each (shifts away from each other), and each state picks up a $V/\Delta E = 10\%$ amplitude admixture of the other. If the splitting were $\lesssim 1$ MHz you'd switch to degenerate theory / exact 2×2 diagonalization.

# Connections

- [[Stark Effect and Light Shifts]] — this machinery's most-used AMO output
- [[Time-Dependent Perturbation Theory]] — same expansion when $V$ oscillates
- [[Two-Level Systems]] — the exact 2×2 answer perturbation theory approximates (and the fallback near degeneracy)
- [[Rayleigh Quotient and Variational Principle]] — the complementary non-perturbative estimate

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §5.1–5.2
