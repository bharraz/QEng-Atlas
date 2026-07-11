 #AMO

**The optical wavelength dwarfs the atom, so the field is uniform across it: set $e^{i\mathbf{k}\cdot\mathbf{r}} \approx 1$ and the interaction collapses to $H = -\mathbf{d}\cdot\mathbf{E}$.** The neglected phase is not garbage, though — for a trapped ion it comes back as the entire sideband toolbox.

# Reference

Matrix elements of the full coupling carry $e^{i\mathbf{k}\cdot\mathbf{r}}$; across an atom,

$$k\,a_0 \sim \frac{2\pi a_0}{\lambda} \sim 10^{-3} \quad (\lambda \sim 500\ \mathrm{nm})$$

so to zeroth order

$$H_{\mathrm{int}} = -\,\mathbf{d}\cdot\mathbf{E}(t), \qquad \Omega = \frac{\langle e|\mathbf{d}\cdot\hat{\epsilon}|g\rangle E_0}{\hbar}$$

**First-order corrections** in $\mathbf{k}\cdot\mathbf{r}$ split into magnetic dipole (M1) + electric quadrupole (E2) pieces — rates down by $(k a_0)^2 \sim 10^{-6}$, which is exactly why "forbidden" clock transitions live for seconds.

**The trapped-ion caveat — two different $\mathbf{r}$'s:** the *internal* electron coordinate (relative to the nucleus) justifies the expansion above. But the *center-of-mass* coordinate of the ion in the trap also sits inside $e^{i\mathbf{k}\cdot\mathbf{R}}$, and there the phase must be kept: $\hat{R}$ is an operator on the motional state, $k\hat{x} = \eta(a + a^\dagger)$ with $\eta$ small but its effects resonantly selectable. Dropping it would erase recoil, sidebands, and every motional gate — Lamb–Dicke physics is precisely *not* making the dipole approximation on the COM.

> [!question]- The dipole approximation is excellent for a Ca⁺ ion, yet you drive $|n\rangle \to |n-1\rangle$ motional transitions with light. Contradiction?
> No — the approximation is on the electron's coordinate relative to the nucleus ($k a_0 \sim 10^{-3}$, negligible). The COM position over the laser phase front is a separate factor $e^{ik\hat{x}}$, kept exactly; its $\eta(a + a^\dagger)$ expansion generates the sidebands.

# Connections

- [[Selection Rules]] — E1 rules are the dipole approximation's angular-momentum content; M1/E2 are its corrections
- [[Lamb-Dicke Regime]] — the kept $e^{ik\hat{x}}$ on the COM, expanded in $\eta$
- [[Multipole Expansion]] — the same long-wavelength hierarchy in classical radiation language

---
Source: Foot, *Atomic Physics*, §7.1
