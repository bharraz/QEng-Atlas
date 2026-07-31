#quantum-info

**The most general Markovian evolution of a density matrix: Hamiltonian flow plus dissipators, one per way the environment can kick the system.** If your noise is memoryless, this is the equation — the GKSL theorem says any generator preserving CPTP has exactly this form.

# Reference

$$
\frac{d\rho}{dt} = -\frac{i}{\hbar}[H, \rho] + \sum_k \left( L_k \rho L_k^\dagger - \tfrac12 \{ L_k^\dagger L_k, \rho \} \right)
$$

$\rho$ = density matrix (dimensionless, $\mathrm{Tr}\,\rho = 1$); $H$ = Hamiltonian (J) generating the reversible part; $L_k$ = jump (Lindblad) operators, one per independent decay channel, each carrying $\sqrt{\text{rate}}$ so that $L^\dagger L$ has units of s⁻¹ — this is why $L = \sqrt{\Gamma}\,\sigma_-$ and not $\Gamma\sigma_-$. The rate appears *squared in the operator, linear in the equation*, which is the usual source of factor-of-2 errors.

Anatomy of the dissipator $\mathcal{D}[L]$: **$L\rho L^\dagger$ is the jump** (population arriving after the environment "clicked"); **the anticommutator is the no-jump drain** that keeps $\mathrm{Tr}\,\rho = 1$ — drop either piece and you lose positivity or trace.

**Assumptions (Born–Markov + secular)**: weak system–bath coupling so the bath stays unentangled and unperturbed ($\rho_{SB} \approx \rho \otimes \rho_B$); bath correlation time $\ll$ system relaxation time, so the bath has no memory; RWA on system frequencies for the diagonal GKSL form. **Breaks for**: strong coupling, structured/narrow-band baths, $1/f$ noise (memory! — that's why echo works but Lindblad-with-constant-$\gamma$ can't describe it).

**Standard jump operators:**

| Process | $L$ | Rate observable |
|---|---|---|
| Spontaneous decay | $\sqrt{\Gamma}\,\sigma_-$ | $T_1 = 1/\Gamma$ |
| Pure dephasing | $\sqrt{\gamma_\varphi/2}\,\sigma_z$ | adds $\gamma_\varphi$ to $1/T_2$ |
| Thermal oscillator | $\sqrt{\Gamma(\bar n + 1)}\,a$, $\sqrt{\Gamma \bar n}\,a^\dagger$ | cooling vs heating balance |

**Trajectories unravelling**: Lindblad = ensemble average of stochastic pure-state evolution under $H_{\text{eff}} = H - \tfrac{i\hbar}{2}\sum_k L_k^\dagger L_k$ interrupted by random jumps $|\psi\rangle \to L_k|\psi\rangle/\|\cdot\|$ — simulate with state vectors ($2^n$) instead of density matrices ($4^n$), and each trajectory is what a single continuously-monitored run looks like.

Vectorized, this is just a linear ODE: $d|\rho\rangle\rangle/dt = \mathcal{L}|\rho\rangle\rangle$, so steady states and decay rates are an eigenproblem of the superoperator.

> [!question]- Why can't dissipation be modeled by just adding an anti-Hermitian part to $H$?
> Non-Hermitian $H_{\text{eff}}$ alone leaks trace — it describes conditional no-jump evolution. The $L\rho L^\dagger$ term puts the lost population back where the jump lands; the GKSL structure is exactly what's forced by demanding the map stay CPTP at all times.

# Connections

- [[Quantum Channels]] — $e^{\mathcal{L}t}$ is a CPTP map; Lindblad is its generator
- [[T1 and T2]] — how these rates appear on the Bloch sphere and in the lab
- [[Optical Bloch Equations]] — this equation for a driven two-level atom, written in Bloch-vector components
- [[Vectorization and Superoperators]] — the flattening that turns it into linear algebra
- [[Spontaneous Emission and Linewidth]] — where $\sqrt{\Gamma}\sigma_-$ physically comes from

---
Source: Wiseman & Milburn, *Quantum Measurement and Control*, Ch. 3
