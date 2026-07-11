#EnM

**When a wave is pushed where it can't propagate, k goes imaginary: the field doesn't vanish, it decays exponentially while carrying no power** — unless you catch it within a decay length, in which case it happily resumes propagating (frustration/tunneling).

# Reference

Whenever the dispersion relation demands $k^2 < 0$ in some direction:

$$
e^{ikz} \to e^{-\kappa z}, \qquad E(z) = E_0\,e^{-z/\ell}, \quad \ell = 1/\kappa
$$

Pure evanescent fields are **reactive**: time-averaged Poynting flux along the decay direction is zero (E and H are 90° out of phase) — energy stored, not transmitted. Bring a second propagating medium within ~ℓ and the wave **tunnels**: frustrated total internal reflection, the photon's version of quantum tunneling (mathematically identical).

**Where they appear, with decay lengths:**

| Situation | Decay length ℓ |
|---|---|
| TIR beyond critical angle | $\frac{\lambda}{2\pi\sqrt{n_1^2\sin^2\theta - n_2^2}}$ — a fraction of λ, diverges at θ_c |
| Waveguide below cutoff | $\to c/\omega_c$ well below cutoff (~guide dimension/π) |
| Metal below plasma frequency | $c/\omega_p$ ≈ 25 nm |
| Skin effect (lossy version) | δ, with propagating phase mixed in |

**Working consequences:** fiber cladding must be many ℓ thick or light leaks between cores (that leakage, done on purpose, is a fused fiber coupler); prism/evanescent coupling injects light into waveguides and resonators; near-field microscopy (NSOM/TIRF) uses the sub-λ confinement to beat diffraction; honeycomb shield vents work because below-cutoff decay is exponential in depth. Rule: nothing within a few ℓ = total reflection; anything conducting or refracting inside ℓ changes the answer.

> [!question]- Two fibers' cores brought within a few μm exchange power even though each totally internally reflects. Where does the power cross?
> Through the overlapping evanescent tails in the cladding gap. Alone, each tail carries no power; with the second core inside the decay length, the boundary problem changes and net flux tunnels across — frustrated TIR, the basis of fused couplers.

# Connections

- [[Total Internal Reflection and Brewster Angle]] — the canonical evanescent field beyond θ_c
- [[Waveguides]] — below-cutoff modes are evanescent; exploited for shield penetrations
- [[Plasma Frequency and Drude Model]] — why field in a metal below ω_p is evanescent, making metals mirrors
- [[Optical Fibers and Fiber Coupling]] — guided modes have evanescent cladding tails; couplers and bend loss live there
- [[Skin Depth]] — the lossy-conductor cousin: decay with phase, power dissipated rather than reflected

---
Source: Griffiths, *Introduction to Electrodynamics*, §9.3.3; Jackson §7.4
