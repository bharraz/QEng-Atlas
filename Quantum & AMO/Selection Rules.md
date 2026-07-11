#quantum #AMO

**Selection rules are conservation of angular momentum and parity applied to the photon: E1 light carries one unit and odd parity, so only transitions matching that can go — everything else needs a higher multipole and is slow.** "Forbidden" means slow, and slow is what clock and shelving transitions are made of.

# Reference

**E1 (electric dipole) rules:**

| quantity | rule | notes |
|---|---|---|
| parity | must flip | dipole operator is odd — the origin of everything below |
| $\Delta l$ | $\pm 1$ | parity flip + one unit of photon angular momentum |
| $\Delta J$, $\Delta F$ | $0, \pm 1$ | but $J{=}0 \not\to J{=}0$, $F{=}0 \not\to F{=}0$ |
| $\Delta m$ | $0$ ($\pi$), $\pm 1$ ($\sigma^\pm$) | set by polarization relative to $\mathbf{B}$ axis |

**Polarization decoder** (quantization axis along $\mathbf{B}$): linear ∥ $\mathbf{B}$ drives $\pi$ ($\Delta m = 0$); circular about $\mathbf{B}$ drives $\sigma^+$ or $\sigma^-$; linear ⊥ $\mathbf{B}$ is an equal $\sigma^+ + \sigma^-$ mix. Geometry errors here are why your "pure $\pi$" pulse leaks population — the $m$-resolved amplitudes are Clebsch–Gordan factors, and misalignment turns nominally-zero ones on.

**When E1 is forbidden**, M1 (parity-even, $\Delta l = 0$) and E2 (parity-even, $\Delta l = 0, \pm 2$) take over, suppressed by $\sim \alpha^2$ or $(ka_0)^2$ in rate: lifetimes jump from ns to ms–s. That's the feature: $S_{1/2} \to D_{5/2}$ quadrupole lines in Ca⁺/Sr⁺/Ba⁺ ($\sim$ 1 s lifetimes) make Hz-linewidth optical qubits and clocks.

> [!question]- Why can't a $J=0 \to J=0$ transition go by E1 even though $\Delta J = 0$ is allowed?
> The photon carries one unit of angular momentum; two $J=0$ states can't absorb it — the triangle rule $|J - 1| \le J' \le J + 1$ has no $J'=0$ solution from $J=0$ with $k=1$. It's the Clebsch–Gordan zero, not parity.

# Connections

- [[Clebsch-Gordan Coefficients]] — the rules are exactly the vanishing conditions of $\langle J m; 1 q | J' m'\rangle$
- [[Dipole Approximation]] — E1 dominance comes from $e^{ik\cdot r} \approx 1$; its corrections are M1/E2
- [[Optical Pumping]] — engineering these rules to funnel population into one state
- [[Multipole Expansion]] — the classical ancestor of the E1/M1/E2 hierarchy

---
Source: Foot, *Atomic Physics*, §2.2 & §5.4
