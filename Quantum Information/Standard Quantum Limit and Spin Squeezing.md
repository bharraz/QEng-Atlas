#quantum-info #metrology

**The standard quantum limit $\Delta\phi = 1/\sqrt{N}$ is what uncorrelated particles give; entanglement can reach $1/N$; and entanglement-enhanced sensing is the problem of gaining variance in the generator without gaining equal fragility to decoherence.** The bound itself is on [[Fisher Information and the Cramér-Rao Bound]]. In practice the Heisenberg limit is mostly *not* achieved, because the states that approach it are the most fragile to decoherence.

# Reference

**The Bloch-sphere picture of the SQL.** $N$ spins along $x$ form a collective spin $J = N/2$ with transverse uncertainty $\Delta J_{y,z} = \sqrt{N}/2$ — the **coherent spin state**, whose uncertainty disk is the projection noise. A phase rotates the vector by $\phi$; resolvable rotation = disk size / vector length:

$$\Delta\phi_{\text{SQL}} = \frac{\Delta J_\perp}{|J|} = \frac{1}{\sqrt{N}}.$$

**Picture:** $N$ independent spins as $N$ coin flips: the readout noise grows as $\sqrt N$ while the signal grows as $N$, so the phase error falls as $1/\sqrt N$; correlating the spins lets the noise grow more slowly.

**Spin squeezing** redistributes the disk: shrink the noise along the readout quadrature at the expense of the other (Heisenberg only constrains the *product*). The **Wineland parameter** is the operational figure of merit —

$$\xi^2 = \frac{N\,(\Delta J_\perp)^2_{\min}}{\langle J \rangle^2}, \qquad \Delta\phi = \frac{\xi}{\sqrt{N}},$$

metrological gain in dB $= -10\log_{10}\xi^2$. $\xi^2$ also penalizes lost contrast ($\langle J\rangle$ in the denominator): a state squeezed in variance but decohered in length gains nothing. $\xi^2 < 1$ is also an **entanglement witness** — no separable state beats the SQL, so a measured 3 dB of metrological gain *is* a certificate of useful entanglement.

**How squeezing is made:** one-axis twisting $H \propto \chi J_z^2$ (the nonlinearity shears the disk — implemented via cavity-mediated interactions in atomic ensembles, the MS-type interaction in ion chains, or collisions in BECs); or quantum non-demolition measurement (measure $J_z$ optically with resolution below the projection noise — the measurement itself squeezes the conditional state).

**GHZ / NOON states — the $1/N$ endpoint and its price.** The GHZ state's $F_Q = N^2$ comes from its two branches accumulating phase $N$ times faster ($e^{iN\phi}$ fringes — which also means an $N$-fold shorter unambiguous phase range; you must already know the phase to within $2\pi/N$). The price is the deal-breaker: single-particle decoherence at rate $\gamma$ dephases the $N$-particle coherence at $N\gamma$. Coherence time drops as $1/N$ exactly as sensitivity gains $\sqrt{N}$ (over SQL), and for phase accumulated over an *optimized* interrogation time the two effects cancel:

$$\boxed{\text{under Markovian dephasing, the optimal gain over SQL is a constant factor } (\le\sqrt{e} \text{ in } \Delta\phi), \text{ not a scaling.}}$$

This single result explains the shape of the field: nobody chases raw Heisenberg scaling in noisy systems; the literature is about *modest, robust* gains (squeezing at fixed contrast), noise with structure that evades the no-go (non-Markovian, correlated), or short-time regimes where the trade hasn't bitten yet.

**Photonic dictionary:** identical structure with quadratures for spin components — squeezed light beats shot noise at the dark port (gravitational-wave detectors inject squeezed light as standard practice); NOON states are photonic GHZ, and equally fragile (one lost photon reveals which path → coherence gone).

**Sensitivity bookkeeping** (assembling the vault's pieces): per-√Hz sensitivity = $\Delta\phi$ per shot × slope conversion ÷ $\sqrt{\text{shot rate}}$, then [[Allan Variance]] tells you how it integrates down and where drift takes over; $T_2$ caps the interrogation time (hence $\eta \propto 1/\sqrt{T_2}$ in the [[NV Centers (atlas)|NV formula]]); squeezing multiplies the entire thing by ξ.

> [!question]- A colleague claims 10 dB of spin squeezing but their clock only improved 3 dB. What's the usual story?
> The 10 dB is likely the *noise-variance* reduction $(\Delta J_z^2)$, not the Wineland ξ² — the squeezing interaction and subsequent handling also curled and shortened the mean spin (one-axis twisting wraps the disk around the sphere; technical noise decoheres it), costing contrast that ξ² charges for but the variance number hides. Additionally the clock may not be projection-noise-limited in the first place (local-oscillator/Dick noise); squeezing only helps the noise that was quantum. Check: quote ξ², and verify the unsqueezed clock sat at the SQL.

# Connections

- [[Fisher Information and the Cramér-Rao Bound]] — the general bound that the SQL and Heisenberg limit are cases of
- [[Quantum Sensing]] — where the SQL/Heisenberg distinction lands in a real sensing sequence
- [[Squeezed States]] — the photonic quadrature version
- [[Bell States]] / [[Entanglement Measures]] — GHZ structure; ξ² < 1 as a witness
- [[Molmer-Sorensen Gate]] — the $J^2$-type interaction that twists ion ensembles
- [[Ramsey Interferometry]] — the protocol all of this plugs into
- [[Allan Variance]] — from per-shot Δφ to stability curves
- [[T1 and T2]] — the decoherence that sets the optimal interrogation time

---
Source: Wineland et al., *Phys. Rev. A* 50, 67 (1994); Pezzè et al., "Quantum metrology with nonclassical states of atomic ensembles," *Rev. Mod. Phys.* 90, 035005 (2018); Huelga et al., *Phys. Rev. Lett.* 79, 3865 (1997) (the decoherence no-go)
