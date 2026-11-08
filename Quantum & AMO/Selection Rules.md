#quantum #AMO

**An atom absorbing or emitting a photon must balance angular momentum and parity with it: an electric-dipole (E1) photon carries one unit of angular momentum and odd parity, so only transitions that match can proceed quickly, and everything else needs a higher multipole and is slow.** "Forbidden" means slow, not impossible — and the slow transitions are what optical clocks, optical qubits, and shelving levels are made of.

# Reference

**The origin.** A transition amplitude $\langle f|\hat O|i\rangle$ vanishes unless the symmetry labels of the final state, the operator, and the initial state combine to something invariant ([[Symmetry in Quantum Mechanics]]). For atoms the symmetries are rotations (angular momentum) and inversion (parity); the E1 operator $\vec d$ is a rank-1 tensor with odd parity ([[Parity and Time Reversal]], [[Wigner-Eckart Theorem]]).

**Picture:** the photon is a package with a fixed spin and a fixed handedness — the atom can absorb it only if the change in its own state can hold exactly that package.

**E1 (electric dipole) rules:**

| Quantity | Rule | Notes |
|---|---|---|
| parity | must change | the dipole operator is odd — the origin of everything below |
| $\Delta l$ | $\pm 1$ | parity change plus one unit of photon angular momentum |
| $\Delta J$, $\Delta F$ | $0, \pm 1$ | but $J{=}0 \not\to J{=}0$, $F{=}0 \not\to F{=}0$ |
| $\Delta m$ | $0$ ($\pi$), $\pm 1$ ($\sigma^\pm$) | set by polarization relative to the $\mathbf{B}$ axis |

**Polarization decoder** (quantization axis along $\mathbf{B}$): linear polarization ∥ $\mathbf{B}$ drives $\pi$ ($\Delta m = 0$); circular about $\mathbf{B}$ drives $\sigma^+$ or $\sigma^-$; linear ⊥ $\mathbf{B}$ is an equal $\sigma^+ + \sigma^-$ mix. Geometry errors here are why a nominally pure $\pi$ pulse leaks population: the $m$-resolved amplitudes are Clebsch–Gordan factors, and misalignment turns on amplitudes that should be zero ([[Clebsch-Gordan Coefficients]]).

**When E1 is forbidden**, M1 (parity-even, $\Delta l = 0$) and E2 (parity-even, $\Delta l = 0, \pm 2$) take over, suppressed in rate by about $\alpha^2$ or $(ka_0)^2$. Lifetimes jump from ns to ms–s. The $S_{1/2} \to D_{5/2}$ quadrupole lines in Ca⁺, Sr⁺, and Ba⁺, with lifetimes of order 1 s, give Hz-linewidth optical qubits and clocks.

| Multipole | Parity change | Angular momentum carried | Rate relative to E1 |
|---|---|---|---|
| E1 | yes | 1 | 1 |
| M1 | no | 1 | $\sim\alpha^2$ |
| E2 | no | 2 | $\sim(ka_0)^2$ |
| M2, E3 | yes | 2, 3 | further suppressed |

**Other routes around a rule:**
- **Two-photon and Raman transitions** use two E1 steps, so parity is unchanged overall and $\Delta l = 0, \pm2$ ([[Raman Transitions]]).
- **State mixing** lends strength to a forbidden line: a small admixture of an allowed state, from hyperfine coupling or an applied field, makes the transition weakly allowed. The Al⁺ clock transition $^1S_0 \to {}^3P_0$ proceeds through hyperfine mixing ([[Time-Independent Perturbation Theory]]).
- **$J = 0 \to J = 0$** is forbidden for single photons of every multipole, since a photon always carries at least one unit of angular momentum.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| lifetime of an excited level | the lowest multipole available: ns for E1, ms–s for E2 or M1 |
| which $m$-components appear for a given polarization | the polarization purity and the field alignment |
| a line that appears only with a field applied | a field-induced admixture of an allowed state |
| relative strengths of the components of a multiplet | Clebsch–Gordan factors, a check on the level assignment |

> [!question]- Why can't a $J=0 \to J=0$ transition go by E1 even though $\Delta J = 0$ is allowed?
> The photon carries one unit of angular momentum, and two $J=0$ states cannot absorb it: the triangle rule $|J - 1| \le J' \le J + 1$ has no $J'=0$ solution from $J=0$ with $k=1$. It is a Clebsch–Gordan zero, not a parity rule.

# Connections

- [[Clebsch-Gordan Coefficients]] — the rules are the vanishing conditions of $\langle J m; 1 q | J' m'\rangle$
- [[Dipole Approximation]] — E1 dominance comes from $e^{ik\cdot r} \approx 1$; its corrections are M1 and E2
- [[Optical Pumping]] — using these rules to move population into one state
- [[Multipole Expansion (Atlas)]] — the classical ancestor of the E1/M1/E2 hierarchy
- [[Symmetry in Quantum Mechanics]] — the general vanishing-integral rule these are cases of
- [[Parity and Time Reversal]] — the parity half of the rules
- [[Wigner-Eckart Theorem]] — the angular-momentum half, with relative strengths

---
Source: Foot, *Atomic Physics*, §2.2 & §5.4
